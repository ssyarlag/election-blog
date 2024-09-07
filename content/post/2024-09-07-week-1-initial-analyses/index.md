---
title: Week 1 - Initial Analyses
author: Package Build
date: '2024-09-07'
slug: week-1-initial-analyses
categories: []
tags: []
---

In this first blog post, I begin by conducting some initial analyses of the American elections. Using data from 1948-2020, I analyze how competitive elections are and the proportion of states that vote blue/red. My thanks to Matt Dardet for writing much of this code during and before our weekly section, as well as ShuXin Ho for helping me identify latitude/longitude loading bugs in my maps.


## Questions:
## 1: How competitive are presidential elections in the United States?
## 2: Which states vote blue/red and how consistently

To answer this question, we began by observing general trends in preference for either of the two major parties' candidates between 1948 and 2020. We conducted analyses at both the national and state level. For the former, we produced a line plot of the two-party vote share per party in each election. For the latter, we used a map to visually break down the total percentage in the line plot by state, showing which candidate won each state in each election. 



``` r
library(ggplot2)
library(maps)
library(tidyverse)
```

```
## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
## ✔ dplyr     1.1.4     ✔ readr     2.1.5
## ✔ forcats   1.0.0     ✔ stringr   1.5.1
## ✔ lubridate 1.9.3     ✔ tibble    3.2.1
## ✔ purrr     1.0.2     ✔ tidyr     1.3.1
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
## ✖ purrr::map()    masks maps::map()
## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
```

``` r
# Load in data
d_popvote <- read_csv('popvote_1948-2020.csv')
```

```
## Rows: 38 Columns: 9
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr (2): party, candidate
## dbl (3): year, pv, pv2p
## lgl (4): winner, incumbent, incumbent_party, prev_admin
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

``` r
# Create pivoted dataset and add winner column
d_popvote_wide <- d_popvote |>
  select(year, party, pv2p) |>
  pivot_wider(names_from = party, values_from = pv2p) |>
  mutate(winner = ifelse(democrat > republican, "D", "R"))
```


``` r
# Line plot demonstrating percentage of two-party popular vote per party 
line_plot_win_trend <- d_popvote |>
  ggplot(mapping = aes(x = year, y = pv2p, color = party)) +
  geom_line() +
  scale_color_manual(values = c("dodgerblue4", "firebrick1")) +
  theme_bw() +
  labs(title = "Percentage of Two-Party Popular Vote by Party, 1948-2020",
       x = "Year",
       y = "Two-Party Vote Percentage",
       color = "Party")

# Loading state data for map and formatting for compatibility
states_map <- map_data("state")
d_pvstate_wide <- read_csv("clean_wide_state_2pv_1948_2020.csv")
```

```
## Rows: 959 Columns: 14
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr  (1): state
## dbl (13): year, D_pv, R_pv, D_pv2p, R_pv2p, D_pv_lag1, R_pv_lag1, D_pv2p_lag...
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

``` r
d_pvstate_wide$region = tolower(d_pvstate_wide$state)

# Creating new dataframe with winners highlighted
pop_2p_vote_w_state <- d_pvstate_wide |>
  left_join(states_map, by = "region") |>
  mutate(winner = ifelse(D_pv2p > R_pv2p, "D", "R"))
```

```
## Warning in left_join(d_pvstate_wide, states_map, by = "region"): Detected an unexpected many-to-many relationship between `x` and `y`.
## ℹ Row 1 of `x` matches multiple rows in `y`.
## ℹ Row 1 of `y` matches multiple rows in `x`.
## ℹ If a many-to-many relationship is expected, set `relationship =
##   "many-to-many"` to silence this warning.
```

``` r
# Map of Two Party Popular Vote Winners by State
pop_2p_vote_winner_by_year_map <- pop_2p_vote_w_state |>
  ggplot(mapping = aes(x = long, y = lat, group = group)) + geom_polygon(aes(fill = winner), color = "black") +
  scale_fill_manual(values = c("dodgerblue4", "firebrick1")) +
  facet_wrap(~year)+
  theme_void() +
  labs(title = "Two-Party Popular Vote Winners by State by Year")

line_plot_win_trend
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-2-1.png" width="672" />

``` r
pop_2p_vote_winner_by_year_map
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-2-2.png" width="672" />
Then, to measure the competitiveness of each states in recent years, I produced the following map, demonstrating the average two-party popular vote margin in each state in each election following 2008. I chose this cutoff to reflect modern trends in state-party alignment, especially in the era of Trump.


``` r
pop_2p_vote_by_state_post2008 <- pop_2p_vote_w_state |>
  filter(year > 2008) |>
  mutate(margin = D_pv2p - R_pv2p) |>
  group_by(state, group, order, lat, long) |>
  summarize(average_margin = mean(margin))
```

```
## `summarise()` has grouped output by 'state', 'group', 'order', 'lat'. You can
## override using the `.groups` argument.
```

``` r
map_pop_2p_vote_by_state_post2008 <- pop_2p_vote_by_state_post2008 |>
  ggplot(mapping = aes(x=long, y = lat, group = group)) +
  geom_polygon(aes(fill = average_margin), color = "black") +
  scale_fill_gradient2(high= "dodgerblue4",
                       mid = "purple3",
                       low = "firebrick1",
                       breaks = c(-50, -25, 0, 25, 50),
                       limits = c(-50,50)) +
  theme_void() +
  labs(title = "States by Average Two-Party Vote Share Margin post 2008",
       gradient = "Average Margin")


map_pop_2p_vote_by_state_post2008
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />

States that are more red on this map have consistently tended to overwhelmingly vote Republican, while those that are more blue have consistently voted overwhelmingly Democrat. While states like California and Wyoming appear to often regularly vote Democrat and Republican respectively, it is interesting to observe cases like Ohio or Michigan, which may tend to lean Republican or Democrat, but have a much smaller margin. Such states with smaller margins appear to also be more competitive, based on recent historical trends. 

To better understand what actually constitutes a swing state, I also plo



---
title: Week 1 - Initial Analyses
author: Package Build
date: '2024-09-07'
slug: week-1-initial-analyses
categories: []
tags: []
---

In this first blog post, I begin by conducting some initial analyses of the American elections. Using data from 1948-2020, I analyze how competitive elections are and the proportion of states that vote blue/red. My thanks to Matt Dardet for writing much of this code during and before our weekly section, as well as ShuXin Ho for helping me identify latitude/longitude loading bugs in my maps.



We began by producing a general line plot showing trends in two-party vote share for each party between 1948 and 2020, as well as a map of state election winners by year. Both of these are demonstrated below


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
line_plot_win_trend <- d_popvote |>
  ggplot(mapping = aes(x = year, y = pv2p, color = party)) +
  geom_line() +
  scale_color_manual(values = c("dodgerblue4", "firebrick1")) +
  theme_bw() +
  labs(title = "Percentage of Popular Vote by Party, 1948-2020",
       x = "Year",
       y = "Two-Party Vote Percentage",
       color = "Party")

states_map <- map_data("state")
```




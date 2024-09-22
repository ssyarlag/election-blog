---
title: Week 3 - Polling
author: Package Build
date: '2024-09-19'
slug: week-3-polling
categories: []
tags: []
---

In this week's post, we focus on analyzing polling data, attempting to understand how they can best predict election outcomes. My thanks again to Matthew Dardet for his generous starter code.

For the purpose of this analysis, we looked at polling data from the 2020 election (sourced from FiveThirtyEight). While election forecasting might benefit from more data, we reference 2020 here for simplicity. We began by visualizing the available data, helping us understand existing patterns.



<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-2-1.png" width="672" />
This data shows that polling averages shift over the months before the election, perhaps being affected by events that happened during the election cycle. For example, we see a substantial decline in support for Donald Trump around June 2020 - perhaps corresponding to the murder of George Floyd (1).

However, it is interesting to see if election forecasts made using polling data in the few weeks prior to the election are necessarily more predictive of the final outcomes than prior weeks. Some, such Tien and Lewis-Beck, claim that "short-view forecasts," which solely rely on polling data, especially in the weeks prior to the election, tend to be inaccurate (2).

To test the accuracy of November polls, we computed several regressions of November polling averages on actual election outcomes between 1968 and 2020 (we have data as early as 1948, but we drop earlier years given that we do not have polling data from FiveThirtyEight). I calculated three separate regressions, highlighted in the table below, which model predictions for only Democratic candidates, only Republicans, and both parties. 



![](images/novpolls.jpg)


Given that the Republican only model has an R^2 value of 0.727 while the Democrat only model has an R^2 value of 0.665 (with the combined model being in between), it appears that polling data from FiveThirtyEight has, on average, been more predictive of Republican outcomes. However, I also wanted to see if the relationship may have been skewed by earlier polling data, which was likely less accurate. 

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-4-1.png" width="672" />

This scatterplot, which includes a line demonstrating perfect poll prediction, shows that November polls often underpredict candidate performance. This led me to calculate the years/candidates with the lowest November prediction error.



| Year|Party |Candidate         | Two-Party Vote Share| Final Poll Prediction of Vote Share| Prediction Error|
|----:|:-----|:-----------------|--------------------:|-----------------------------------:|----------------:|
| 2012|REP   |Romney, Mitt      |                48.08|                               47.75|            -0.34|
| 2020|DEM   |Biden, Joseph R.  |                52.27|                               51.85|            -0.42|
| 1988|REP   |Bush, George H.W. |                53.83|                               52.29|            -1.54|
| 2004|DEM   |Kerry, John       |                48.73|                               46.98|            -1.75|
| 1984|DEM   |Mondale, Walter   |                40.88|                               38.95|            -1.93|
| 1984|REP   |Reagan, Ronald    |                59.12|                               56.92|            -2.20|
| 2008|REP   |McCain, John      |                46.23|                               43.82|            -2.41|
| 2004|REP   |Bush, George W.   |                51.27|                               48.60|            -2.67|
| 1968|REP   |Nixon, Richard M. |                50.40|                               47.72|            -2.68|
| 2008|DEM   |Obama, Barack H.  |                53.77|                               50.99|            -2.78|


This shows two interesting conclusion. First, all of the closest predictions have underpredicted candidate performance. Second, recent polls haven't  always been more successful. In fact, polling from 1968, the earliest year in our dataset, makes our top 10. While many recent years make up our top 10, this may lend credence to the argument that there are certain "fundamentals" that can help predict voter performance, regardless of the degree of accurate data and statistical/computing power that pollsters may have access to (2). 

Given this, we also wanted to explore if polls at other times in an election cycle better predict actual election outcomes. To do so, we observed week-level poll data, aiming to identify which weeks were most predictive. To do so, we used the regularization method of Elastic Net, identifying the most predictive weeks.

I trained this model using data from before 2020, evaluating it on the data from 2020. I did this because although we do have some data from 2024, the change in the Democratic presidential candidate midway through the cycle may complicate results, combined with the fact that we do not have a completed election, may complicate results. 


| Prediction Error - Democratic Party (2020)| Prediction Error - Republican Party (2020)|
|------------------------------------------:|------------------------------------------:|
|                                   2.119166|                                  0.5729736|


Our model predicted that, based on polling trends from previous years, Biden would earn 54.4 % of the two-party popular vote, while Trump would earn 48.3%. While these predictions were slightly high for both candidates, the poll was off by over 2 percentage points for Biden. On one hand, this may be due to the substantial variations between this election and previous ones. However, it may lend further credence to the earlier point that polls tend to overpredict candidate performance. 

Given these findings, it is interesting to compare the perspectives that two major pollsters involved with FiveThirtyEight -- Nate Silver and G. Elliot Morris -- have proposed regarding election forecasting, an *extension* of our previous analytical work.

In a June 2024 article (5), Silver highlights the changes in his 2024 prediction relative to his 2020 predictions. In this, he seems to focus on making minor tweaks to his previous model, saying that he "tend[s] to be conservative about making changes to the election models. He appears to focus on very broad factors that affect election outcomes like party level turnout and incumbency. However, in an article released around the same time (6), Morris encourages considering the fundamentals, but takes a different perspective, considering, for example "the rates of change of these indicators." In doing so, he also delves into greater specificity than Silver, observing characteristics like state effects on neighbors, seeming to stray away from a strict focus on "fundamentals."

# Citations

1. Silverstein, Jason. “The Global Impact of George Floyd: How Black Lives Matter Protests Shaped Movements around the World - CBS News,” June 4, 2021. https://www.cbsnews.com/news/george-floyd-black-lives-matter-impact/.

2. Tien, Charles, and Michael Lewis-Beck. “Evaluating the Long-View Forecasting Models of the 2016 Election.” OUPblog, January 11, 2017. https://blog.oup.com/2017/01/forecasting-models-2016-election/.

3. chemdork123. “Answer to ‘Change Scale on X Axis in Ggplot in R.’” Stack Overflow, July 20, 2020. https://stackoverflow.com/a/63003636.

4. Posit Community. “Add X=y Geom_abline to Ggplot - General,” June 1, 2019. https://forum.posit.co/t/add-x-y-geom-abline-to-ggplot/32154.

5. Silver, Nate. “2024 Presidential Election Model Methodology Update,” June 26, 2024. https://www.natesilver.net/p/model-methodology-2024.

6. Morris, G. Elliott. “How 538’s 2024 Presidential Election Forecast Works.” ABC News, June 11, 2024. https://abcnews.go.com/538/538s-2024-presidential-election-forecast-works/story?id=110867585.

7. GeeksforGeeks. “How to Create Tables in R?,” December 16, 2021. https://www.geeksforgeeks.org/how-to-create-tables-in-r/.

8. “Build a Data Frame — Tibble.” Accessed September 22, 2024. https://tibble.tidyverse.org/reference/tibble.html.



Help documents for Model Summary, Top N, Slice_Max, Abs (Absolute Value)

# Data Sources

Poll Predictions from FiveThirtyEight and National Election Data (both provided by course)


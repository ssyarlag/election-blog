---
title: Week 6 - Campaign Ads
author: Shriya Yarlagadda
date: '2024-10-09'
slug: week-6-campaign-ads
categories: []
tags: []
---
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />




This week, we explore the impact of campaign ads on election outcomes. My thanks as always to Matthew Dardet for his generous starter code. 

I start by including some visualizations, originally put together by Matt, to help better understand advertising trends.

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-2-1.png" width="672" />

It appears that economic themes, including employment, budget, and taxes, are common themes in ads nationwide, potentially suggesting that campaigns believe that information related to the economy is a key topic in the minds of many voters and therefore must be addressed. I was interested, though, in seeing trends in social media ads in more recent elections. Using Facebook data from the most recent presidential election, subsetted to only include advertisements directly launched by the Biden or Trump campaigns, I produced a visualization that compared the number of ads launched, the amount of spending, and polling support over time.





<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-4-1.png" width="672" />


When comparing the graphs, it seems that although the Trump campaign launched more ads over time, they were significantly outspent by the Biden campaign, which may indicate differences in the ad strategies that were used for outreach. However, from a cursory visual view, it doesn't appear that these trends substantially affect polling outcomes. To address this further, I ran a regression of both advertising indicators on polling support for each party.


<table style="NAborder-bottom: 0; width: auto !important; margin-left: auto; margin-right: auto;" class="table">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:center;"> Biden </th>
   <th style="text-align:center;"> Trump </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:center;"> 50.430*** </td>
   <td style="text-align:center;"> 43.373*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.250) </td>
   <td style="text-align:center;"> (0.219) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> spend </td>
   <td style="text-align:center;"> 0.000 </td>
   <td style="text-align:center;"> 0.000** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.000) </td>
   <td style="text-align:center;"> (0.000) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> count </td>
   <td style="text-align:center;"> 0.000* </td>
   <td style="text-align:center;"> 0.000+ </td>
  </tr>
  <tr>
   <td style="text-align:left;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.000) </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.000) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Num.Obs. </td>
   <td style="text-align:center;"> 21 </td>
   <td style="text-align:center;"> 36 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 </td>
   <td style="text-align:center;"> 0.346 </td>
   <td style="text-align:center;"> 0.274 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 Adj. </td>
   <td style="text-align:center;"> 0.273 </td>
   <td style="text-align:center;"> 0.230 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> AIC </td>
   <td style="text-align:center;"> 44.6 </td>
   <td style="text-align:center;"> 101.0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> BIC </td>
   <td style="text-align:center;"> 48.7 </td>
   <td style="text-align:center;"> 107.3 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Log.Lik. </td>
   <td style="text-align:center;"> −18.278 </td>
   <td style="text-align:center;"> −46.488 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> F </td>
   <td style="text-align:center;"> 4.758 </td>
   <td style="text-align:center;"> 6.229 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> RMSE </td>
   <td style="text-align:center;"> 0.58 </td>
   <td style="text-align:center;"> 0.88 </td>
  </tr>
</tbody>
<tfoot><tr><td style="padding: 0; " colspan="100%">
<sup></sup> + p &lt; 0.1, * p &lt; 0.05, ** p &lt; 0.01, *** p &lt; 0.001</td></tr></tfoot>
</table>


Though increased spending appeared to affect Republican support and an increase in total number of ads affected support for both candidates significantly, potentially contradicting my previous finding, the magnitude of this change appeared very very small. While the competitiveness of elections could mean that even very small changes are meaningful (a point mentioned in our recent course lectures), the fact that polling support is not a perfect predictor of election outcomes and our lack of data for other important variables like voter use of Facebook in this situation means that it is hard to draw any meaningful conclusions. A potential future analysis may want to try analyzing this relationship at the state level to increase the power of these conclusions. While our course has access to overall campaign ad coverage and spending data by state and candidate, as well as state level polling data, analyzing this problem in the context of social media is even more difficult, because a social media ad may not hew to geographic boundaries as effectively as a TV or radio ad. One example of this is that while we could develop a proxy for Biden campaign spending in Wisconsin by measuring spending on the page "Wisconsin for Biden," it is unclear if ads from national-level pages may have been more effective in certain geographic regions. 

However, given the data that we do have, if we were to assume that advertising had a limited effect on national level outcomes, this would further the hypothesis (mentioned in our most recent Videocast lecture by Professor Enos, as well as implied by Huber and Arcenaux- 5) that broad methods of advertising may not drive campaign outcomes. Instead, if there is to be a deviation from predictions based on "fundamentals" at all, outreach to voters may need to be more targeted (5). It is also important to acknowledge, though, that we only have access to data from 2020 Facebook campaign ads for the purpose of this course. Perhaps these trends may be different in other elections or if incorporating other forms of online advertising, which notably has the potential to be very targeted (6). 

As I reflect on my previous blogs and create an updated prediction model for this upcoming election, I may consider ad spending as an indicator of a campaign's resources, but not necessarily as an action that could inherently increase candidate support. In other words, I will more heavily rely on indicators like economic considerations, incumbent popularity, and predicted turnout, that we have found to be better predictors in previous weeks. 


# References:

“Answer to ‘How Do I Undo the Most Recent Local Commits in Git?’” 2009. Stack Overflow. https://stackoverflow.com/a/927386.

(1) Pivot Longer Help Page

(2) Firke, Sam. 2015. “Answer to ‘Selecting Data Frame Rows Based on Partial String Match in a Column.’” Stack Overflow. https://stackoverflow.com/a/31273659; 17 Merging | Data Wrangling with R. n.d. Accessed October 13, 2024. https://users.ssc.wisc.edu/~hemken/Rworkshops/dwr/merge-tidy.html.; Wickham, Hadley, Sara Altman, and Bill Behrman. n.d. 6 Advanced Pivoting | Data Wrangling. Accessed October 12, 2024. https://dcl-wrangle.stanford.edu.


(3) Left Join help page; “Dual Y Axis with R and Ggplot2 – the R Graph Gallery.” n.d. Accessed October 14, 2024. https://r-graph-gallery.com/line-chart-dual-Y-axis-ggplot2.html.; “Visualizing Time Series Data with Ggplot2 - Tilburg Science Hub.” n.d. Accessed October 13, 2024. https://tilburgsciencehub.com/topics/visualization/data-visualization/graphs-charts/time-series-ggplot2/.; ale_ish. 2022. “Answer to ‘Correlation of Multiple Time Series among the Same Variables in R.’” Stack Overflow. https://stackoverflow.com/a/71892869.; Sec_Axis help page; Scale Y help page; Stibu. 2017. “Answer to ‘Center Plot Title in Ggplot2.’” Stack Overflow. https://stackoverflow.com/a/42556457.; user3490026. 2016. “Answer to ‘Remove Legend Ggplot 2.2.’” Stack Overflow. https://stackoverflow.com/a/35622358.; “Draw Multiple Time Series in Same Plot in R.” 2021. GeeksforGeeks. June 15, 2021. https://www.geeksforgeeks.org/draw-multiple-time-series-in-same-plot-in-r/.
“Ggplot2 Axis Scales and Transformations - Easy Guides - Wiki - STHDA.” n.d. Accessed October 14, 2024. http://www.sthda.com/english/wiki/ggplot2-axis-scales-and-transformations.


(4) Schmelzer, Christoph Hanck, Martin Arnold, Alexander Gerber, and Martin. n.d.-a. 5.4 Heteroskedasticity and Homoskedasticity | Introduction to Econometrics with R. Accessed October 14, 2024. https://www.econometrics-with-r.org/5.4-hah.html.
———. n.d.-b. 7.1 Hypothesis Tests and Confidence Intervals for a Single Coefficient | Introduction to Econometrics with R. Accessed October 14, 2024. https://www.econometrics-with-r.org/7.1-hypothesis-tests-and-confidence-intervals-for-a-single-coefficient.html.

(5) Enos, Ryan, dir. n.d. Videocast 7: The “Ground Game.” GOV 1347 Videocasts.; Huber, Gregory A., and Kevin Arceneaux. 2007. “Identifying the Persuasive Effects of Presidential Advertising.” American Journal of Political Science 51 (4): 957–77. https://doi.org/10.1111/j.1540-5907.2007.00291.x.


(6) Lau, Wilson. 2024. “What Is Targeted Advertising? | AdRoll.” AdRoll Blog. June 30, 2024. https://www.adroll.com/blog/what-is-targeted-advertising.


# Data Sources:

(1) Advertising Data from Wesleyan Media Project + other Data Providers, as provided by course staff of GOV 1347

(2) Polling Data from FiveThirtyEight Polling Averages, also as provided by course staff of GOV 1347

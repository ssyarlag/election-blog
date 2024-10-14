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




This week, we explore the impact of campaign ads on election outcomes, implementing a Bayesian prediction model. My thanks as always to Matthew Dardet for his generous starter code, especially in the implementation of the Bayesian prediction model. 

I start by including some visualizations and charts, also originally put together by Matt, to help better understand advertising trends.

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-2-1.png" width="672" />
It appears that economic themes, including employment, budget, and taxes, are common themes in ads nationwide, potentially suggesting that campaigns believe that information related to the economy is a key topic in the minds of many voters and therefore must be addressed. I was interested, though, in seeing how this translated into social media ads in more recent elections. Using Facebook data from the most recent presidential election, subsetted to only include advertisements directly launched by the Biden or Trump campaigns, I produced a visualization that compared the number of ads launched, the amount of spending, and polling support over time.





<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-4-1.png" width="672" />




--- 



<table style="NAborder-bottom: 0; width: auto !important; margin-left: auto; margin-right: auto;" class="table">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:center;"> Democratic Party </th>
   <th style="text-align:center;"> Republican Party </th>
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









References:
“Answer to ‘How Do I Undo the Most Recent Local Commits in Git?’” 2009. Stack Overflow. https://stackoverflow.com/a/927386.

(1) Pivot Longer Help Page
(2) Firke, Sam. 2015. “Answer to ‘Selecting Data Frame Rows Based on Partial String Match in a Column.’” Stack Overflow. https://stackoverflow.com/a/31273659; 17 Merging | Data Wrangling with R. n.d. Accessed October 13, 2024. https://users.ssc.wisc.edu/~hemken/Rworkshops/dwr/merge-tidy.html.
(3) Left Join help page; “Dual Y Axis with R and Ggplot2 – the R Graph Gallery.” n.d. Accessed October 14, 2024. https://r-graph-gallery.com/line-chart-dual-Y-axis-ggplot2.html.; “Visualizing Time Series Data with Ggplot2 - Tilburg Science Hub.” n.d. Accessed October 13, 2024. https://tilburgsciencehub.com/topics/visualization/data-visualization/graphs-charts/time-series-ggplot2/.; ale_ish. 2022. “Answer to ‘Correlation of Multiple Time Series among the Same Variables in R.’” Stack Overflow. https://stackoverflow.com/a/71892869.; Sec_Axis help page; Scale Y Manual help page; Stibu. 2017. “Answer to ‘Center Plot Title in Ggplot2.’” Stack Overflow. https://stackoverflow.com/a/42556457.; user3490026. 2016. “Answer to ‘Remove Legend Ggplot 2.2.’” Stack Overflow. https://stackoverflow.com/a/35622358.

(4)



Data Sources:

(1) Wesleyan Media Project - Ad Data

(2) 

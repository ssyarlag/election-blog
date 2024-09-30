---
title: 'Week 4: Incumbency'
author: Shriya Yarlagadda
date: '2024-09-25'
slug: week-4-incumbency
categories: []
tags: []
---
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />

In this week's lab, we explore the impact of candidate or party incumbency on presidential election outcomes. More specifically, we ask "How should we treat the incumbency advantage in our 2024 electoral forecasts?". As always, my thanks to Matthew Dardet for his helpful starter code.




This week, we reviewed a canonically successful model used to predict the advantage of incumbency: the Time for Change Model (TFC) by Alan Abramowitz. This relatively simple model -- an OLS regression with independent variables of Quarter 2 GDP, June Gallup poll approval, and whether or not one is an incumbent -- is modeled here. We exclude 2020 data here, given that (as we have shown in previous blogs) the year is an outlier in terms of GDP growth.

<table style="NAborder-bottom: 0; width: auto !important; margin-left: auto; margin-right: auto;" class="table">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:center;"> Time For Change </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:center;"> 48.212*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (1.070) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Quarterly GDP Growth </td>
   <td style="text-align:center;"> 0.465** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.155) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Incumbency Status </td>
   <td style="text-align:center;"> 2.220+ </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (1.244) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> June Approval Rating </td>
   <td style="text-align:center;"> 0.132*** </td>
  </tr>
  <tr>
   <td style="text-align:left;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.025) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Num.Obs. </td>
   <td style="text-align:center;"> 18 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 </td>
   <td style="text-align:center;"> 0.817 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 Adj. </td>
   <td style="text-align:center;"> 0.777 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> AIC </td>
   <td style="text-align:center;"> 89.3 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> BIC </td>
   <td style="text-align:center;"> 93.8 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Log.Lik. </td>
   <td style="text-align:center;"> −39.673 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> F </td>
   <td style="text-align:center;"> 20.783 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> RMSE </td>
   <td style="text-align:center;"> 2.19 </td>
  </tr>
</tbody>
<tfoot><tr><td style="padding: 0; " colspan="100%">
<sup></sup> + p &lt; 0.1, * p &lt; 0.05, ** p &lt; 0.01, *** p &lt; 0.001</td></tr></tfoot>
</table>

With an R^2 value of 0.82, it appears that this model is quite robust at the national level. To test its accuracy further, I conducted cross-validation testing, as demonstrated below. Again, I am grateful for Matthew Dardet's cross-validation starter code from Week 2 

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />

This plot demonstrates that the model generally tends to produce an accurate prediction of the truth, with most measures of error collecting around 0

Given this, I was interested to see how this model would predict the outcome of the 2024 presidential election. Here, I first assume that Harris maintains the incumbency advantage. Although she is not a sitting president, many still associate Harris with the Biden administration, considering the Biden administration's legacy as hers as well (5). Therefore, it may be reasonable to consider her an incumbent as well. This is especially true if we see the TFC model as a quantification of Achen and Bartels's conception of blame attribution -- the association of an incumbent candidate with the economic situation of their administration, even if they were not directly responsible for that outcome (6). If voters do not seem to care much about direct responsibility, it is conceivable that they could even perceive of those close to a "true" incumbent president as being an incumbent themselves.

However, it is also important to acknowledge that Harris' campaign is actively trying to distance itself from Biden's legacy (5). Their success appears reflected in Harris' relative popularity compared to Biden (7). 


| Incumbent| Non-Incumbent|
|---------:|-------------:|
|     48.93|         46.71|

These results suggest that, if Harris has the incumbent advantage, she will earn 48.93% of the two-party popular vote share, meaning that Trump would earn the remaining 51.07% of the popular vote. However, especially given the extent of variation that was shown in the cross-validation testing, it isn't clear that this is strong evidence of a Trump popular vote victory prediction.

Even if we were to assume that Harris and her campaign are able to distance herself from the Biden administration as she hopes to, this model suggests that she would still fail to gain a plurality of the two-party vote share. In fact, she would earn even less, with a predicted two party popular vote share of 46.71, implying that Trump would earn 53.29%. 

# Extension 

Interestingly, this is the first of my models to predict a Trump victory. I was interested in directly comparing my results to the GDP-Growth only model that we built in Week 2. This model was somewhat successful in predicting vote share in previous elections, especially in comparison to other economic variables that we tested. However, it also offers an interesting comparison, given that TFC is also partially based on GDP growth. While our analysis from week 2 predicted a two-party vote share 51.58% for the Democrats, I trained a slightly different model, training on only incumbent party candidates to parallel my TFC model. 


| Incumbent (TFC)| Non-Incumbent (TFC)| GDP Only|
|---------------:|-------------------:|--------:|
|           48.93|               46.71|    51.58|

Once again, the GDP only model predicts that Harris will earn a plurality of votes. This seems to highlight the importance of voter approval to the TFC model -- something that is also highlighted in the 2020 version of the model, as discussed in our section materials. However, it is also important to note that the June approval ratings that we are using in this model data reflects a time before Harris was the Democratic presidential candidate, meaning that it may not be an entirely predictive model. However, it is interesting that this model found a different result than my previous models.

# Citations:
 
 (1) Hlavac, Marek (2022). stargazer: Well-Formatted Regression and Summary Statistics Tables.
 R package version 5.2.3. https://CRAN.R-project.org/package=stargazer 
 
 (2): Model Summary Package - Help Page
 
 (3): Pivot Longer help page, AndrewGB. 2022. “Answer to ‘Pivot Longer for Only Selected Columns.’” Stack Overflow. https://stackoverflow.com/a/71689942.
sbha. 2020. “Answer to ‘Converting Rows into Columns and Columns into Rows Using R.’” Stack Overflow. https://stackoverflow.com/a/60251029.; “How to Convert Columns of an R Data Frame into Rows?” n.d. Accessed September 29, 2024. https://www.tutorialspoint.com/how-to-convert-columns-of-an-r-data-frame-into-rows. - used in a piece that I ended up removing


(4) joran. 2011. “Answer to ‘How Do I Combine Two Data-Frames Based on Two Columns?’” Stack Overflow. https://stackoverflow.com/a/6709335. - used in a piece I ended up removing

(5) Smith, David. 2024. “‘Running Away from Good News’: Why Is Harris Distancing Herself from Biden’s Record?” The Guardian, September 29, 2024, sec. US news. https://www.theguardian.com/us-news/2024/sep/29/election-biden-harris-administration-record.

(6) Bartels, Larry M., Christopher H. Achen, Larry M. Bartels, and Christopher H. Achen. 2017. Democracy for Realists: Why Elections Do Not Produce Responsive Government. Princeton: Princeton University Press. https://muse.jhu.edu/pub/267/monograph/book/64646.; Matthew Dardet's Section Slides

(7) Nadeem, Reem. 2024. “2. How Americans View Harris, Trump and Biden.” Pew Research Center (blog). August 14, 2024. https://www.pewresearch.org/politics/2024/08/14/how-americans-view-harris-trump-and-biden/.

(8) GeeksforGeeks. “How to Create Tables in R?,” December 16, 2021. https://www.geeksforgeeks.org/how-to-create-tables-in-r/.; “Build a Data Frame — Tibble.” Accessed September 22, 2024. https://tibble.tidyverse.org/reference/tibble.html.

# Data Sources

Economic Data: Federal Reserve Economic Data

Vote Data: National Popular Vote Data

Approval Data: Gallup poll




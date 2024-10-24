---
title: Week 7 - Ground Game
author: Shriya Yarlagadda
date: '2024-10-16'
slug: week-7-ground-game
categories: []
tags: []
---
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />

This week, we focus on exploring the impacts of the "ground game" -- a campaign's strategy of individually reaching out to voters in person. Thank you again to Matt Dardet for his helpful starter code.



For this analysis, I am interested in exploring the relationship between ground-campaign activities and voter turnout. Given that ground campaigns happen on a relatively local level, I focus on my home state of Michigan for my analysis this week, reviewing how the prevalence of field offices and campaign events in 2016 impacted turnout outcomes.

First, I visualized the relationship between field offices/campaign events and county turnout. The first map below indicates the location of field offices (+) and campaign events (∆) associated with each party. The second, put together using a mapping tool developed by the Urban Institute and generously described on their Medium site (1), indicates voter turnout in each county in Michigan. Unfortunately, we do not appear to have county-level turnout data for the 2016 election, so I use 2020 county-level turnout instead. While this is an imperfect metric, especially because of the effects of the COVID-19 pandemic, exploring this relationship could also potentially suggest if there are any long-term effects of the location of a campaign office in a region on future political cycles, or if the effects largely wean as the candidate changes.



<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />

From observing these maps, it does not appear that there is a substantial relationship between the location of 2016 campaign activity and 2020 turnout. In fact, if we look at the southeastern part of the state, where much election activity by both parties was concentrated, we see that there was relatively low electoral turnout in 2020. However, it is also important to recognize that these activities were likely clustered around the city of Detroit. Therefore, even if turnout is low, there still could have been a significant number of voters. In other parts of the state, the relationship seems relatively unclear from just this visual representation. Therefore, we also trained three linear regression models of the relationship between campaign activities and turnout at the national level, including total activity, Republican activity, and Democratic activity. While we have turnout metrics at the county level for 2020, we unfortunately do not have campaign activities measured by county, which is why I regress these two metrics at the national level.


<table style="NAborder-bottom: 0; width: auto !important; margin-left: auto; margin-right: auto;" class="table">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:center;"> All Events </th>
   <th style="text-align:center;"> Democratic Events </th>
   <th style="text-align:center;"> Republican Events </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:center;"> 61.842*** </td>
   <td style="text-align:center;"> 61.533*** </td>
   <td style="text-align:center;"> 61.533*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (1.314) </td>
   <td style="text-align:center;"> (1.274) </td>
   <td style="text-align:center;"> (1.274) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> total_events </td>
   <td style="text-align:center;"> −0.167 </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.116) </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> total_offices </td>
   <td style="text-align:center;"> 0.181* </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.084) </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n_ev_D </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> −0.354 </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> (0.249) </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ev_diff_D_R </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> 0.015 </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> (0.369) </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n_office_D </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> 0.050 </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> (0.226) </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> office_diff_D_R </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> 0.288 </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> (0.220) </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n_ev_R </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> −0.354 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> (0.249) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ev_diff_R_D </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> 0.339 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> (0.262) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n_office_R </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> 0.050 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> (0.226) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> office_diff_R_D </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> −0.338* </td>
  </tr>
  <tr>
   <td style="text-align:left;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.137) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Num.Obs. </td>
   <td style="text-align:center;"> 27 </td>
   <td style="text-align:center;"> 27 </td>
   <td style="text-align:center;"> 27 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 </td>
   <td style="text-align:center;"> 0.195 </td>
   <td style="text-align:center;"> 0.349 </td>
   <td style="text-align:center;"> 0.349 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 Adj. </td>
   <td style="text-align:center;"> 0.128 </td>
   <td style="text-align:center;"> 0.230 </td>
   <td style="text-align:center;"> 0.230 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> AIC </td>
   <td style="text-align:center;"> 173.6 </td>
   <td style="text-align:center;"> 171.8 </td>
   <td style="text-align:center;"> 171.8 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> BIC </td>
   <td style="text-align:center;"> 178.7 </td>
   <td style="text-align:center;"> 179.6 </td>
   <td style="text-align:center;"> 179.6 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Log.Lik. </td>
   <td style="text-align:center;"> −82.783 </td>
   <td style="text-align:center;"> −79.924 </td>
   <td style="text-align:center;"> −79.924 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> F </td>
   <td style="text-align:center;"> 2.911 </td>
   <td style="text-align:center;"> 2.946 </td>
   <td style="text-align:center;"> 2.946 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> RMSE </td>
   <td style="text-align:center;"> 5.19 </td>
   <td style="text-align:center;"> 4.67 </td>
   <td style="text-align:center;"> 4.67 </td>
  </tr>
</tbody>
<tfoot><tr><td style="padding: 0; " colspan="100%">
<sup></sup> + p &lt; 0.1, * p &lt; 0.05, ** p &lt; 0.01, *** p &lt; 0.001</td></tr></tfoot>
</table>

This regression confirms my previous assumptions -- metrics of campaign activity alone largely do not appear to have a significant effect on turnout. However, one important exception to this is the number of total offices (and a greater number of Democratic offices relative to Republican offices) driving overall turnout in a statistically significant manner. This latter result seems to align with Darr and Levendusky's findings that field offices increase turnout (4). However, it is interesting to note that campaign events, unintuitively, appear to decrease turnout, though this result is not statistically significant.

Again, it is important to emphasize that this effect may have been limited because of the time difference between the campaign activities and the measure of turnout. To address this, I also produced a map of campaign events in 2020, compared again with the same map of turnout from before below. Unfortunately, we do not have field office data from 2020, making comparing all three metrics impossible. 

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-5-1.png" width="672" />

Again, there does not appear to be a tangible relationship between just the two variables. However, I produce another regression model to test this outcome using only 2020 data.

<table style="NAborder-bottom: 0; width: auto !important; margin-left: auto; margin-right: auto;" class="table">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:center;"> All Events </th>
   <th style="text-align:center;"> Democratic Events </th>
   <th style="text-align:center;"> Republican Events </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:center;"> 69.499*** </td>
   <td style="text-align:center;"> 67.935*** </td>
   <td style="text-align:center;"> 67.935*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (1.470) </td>
   <td style="text-align:center;"> (1.493) </td>
   <td style="text-align:center;"> (1.493) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> total_events </td>
   <td style="text-align:center;"> 0.080 </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.093) </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n_ev_D </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> 0.198 </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> (0.168) </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ev_diff_D_R </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> −0.926* </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> (0.382) </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> n_ev_R </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> 0.198 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> (0.168) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ev_diff_R_D </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;">  </td>
   <td style="text-align:center;"> 0.728+ </td>
  </tr>
  <tr>
   <td style="text-align:left;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.366) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Num.Obs. </td>
   <td style="text-align:center;"> 20 </td>
   <td style="text-align:center;"> 20 </td>
   <td style="text-align:center;"> 20 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 </td>
   <td style="text-align:center;"> 0.040 </td>
   <td style="text-align:center;"> 0.263 </td>
   <td style="text-align:center;"> 0.263 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 Adj. </td>
   <td style="text-align:center;"> −0.013 </td>
   <td style="text-align:center;"> 0.177 </td>
   <td style="text-align:center;"> 0.177 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> AIC </td>
   <td style="text-align:center;"> 124.0 </td>
   <td style="text-align:center;"> 120.7 </td>
   <td style="text-align:center;"> 120.7 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> BIC </td>
   <td style="text-align:center;"> 126.9 </td>
   <td style="text-align:center;"> 124.7 </td>
   <td style="text-align:center;"> 124.7 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Log.Lik. </td>
   <td style="text-align:center;"> −58.981 </td>
   <td style="text-align:center;"> −56.334 </td>
   <td style="text-align:center;"> −56.334 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> F </td>
   <td style="text-align:center;"> 0.752 </td>
   <td style="text-align:center;"> 3.039 </td>
   <td style="text-align:center;"> 3.039 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> RMSE </td>
   <td style="text-align:center;"> 4.62 </td>
   <td style="text-align:center;"> 4.05 </td>
   <td style="text-align:center;"> 4.05 </td>
  </tr>
</tbody>
<tfoot><tr><td style="padding: 0; " colspan="100%">
<sup></sup> + p &lt; 0.1, * p &lt; 0.05, ** p &lt; 0.01, *** p &lt; 0.001</td></tr></tfoot>
</table>

Once again, most of these results don't indicate significance, except for the metrics of the differences between the number of Democratic and Republican offices in a state, with more Republican offices relative to Democratic offices resulting in higher turnout rates. However, I am not sure what the mechanism is for this finding, especially since the results are the opposite of what we found in the last set of regressions.

The large lack of significance, aside from this difference measure, may lend credence to Kalla and Broockman's 2018 work, which highlights that ground campaigns have a relatively minimal effect on outcomes (5).

Following this analysis, I also began building my own predictive model of electoral outcomes, based on my findings from previous weeks. Through an initial conversation with Matt Dardet, I was inspired to start with a relatively "parsimonious" model -- Alan Abramowitz's Time for Change Model (which is also similar to several other prominent models, as we discussed in our section!). While I still use some parts of this model, including its incorporation of GDP growth, I wanted to build a model that was generalizable to candidates who were not incumbents. Given that our analyses from previous weeks also indicated that metrics like turnout, polling, and federal fund allocation (as discussed by Kriner and Reeves (6)) appeared significant, I included these metrics as well. I also notably excluded metrics related to campaign activities, given the relatively insignificant results that I found when incorporating them this week and last. 

My linear regression model considers GDP growth in the quarter immediately prior to the election (although I use 2nd quarter data when predicting 2024 outcomes since it is the most recent data we have available), unemployment, and candidate incumbency at the national level and poll support five weeks prior to the election, total federal funding allocation since 1984, and turnout in the last presidential election at the state level. Using this model, I aim to predict two-party Democratic vote share. Then, I impute Republican vote share by subtracting the Democratic two-party vote share from 100.  Importantly, I also only used data after 1984, wanting to avoid biasing my findings with results from a time when the American political landscape was significantly different than it is today, as well as the election outcomes of Ronald Reagan's second election (7). I had initially only analyzed data from after 1996 (including total grant allocation since 1996), and still include that subsetted model here for comparison.




<table style="NAborder-bottom: 0; width: auto !important; margin-left: auto; margin-right: auto;" class="table">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:center;"> &amp;nbsp;Post 1984 Data </th>
   <th style="text-align:center;"> &amp;nbsp;Post 1996 Data </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:center;"> 7.278** </td>
   <td style="text-align:center;"> 5.423** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (2.664) </td>
   <td style="text-align:center;"> (1.925) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> GDP_growth_quarterly </td>
   <td style="text-align:center;"> −0.074 </td>
   <td style="text-align:center;"> −0.364*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.063) </td>
   <td style="text-align:center;"> (0.047) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> mean_5_wk_poll_support </td>
   <td style="text-align:center;"> 0.898*** </td>
   <td style="text-align:center;"> 1.144*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.039) </td>
   <td style="text-align:center;"> (0.032) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> total_grant </td>
   <td style="text-align:center;"> 0.000*** </td>
   <td style="text-align:center;"> 0.000* </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.000) </td>
   <td style="text-align:center;"> (0.000) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> turnout_lag1 </td>
   <td style="text-align:center;"> 0.022 </td>
   <td style="text-align:center;"> 0.049 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.041) </td>
   <td style="text-align:center;"> (0.032) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> unemployment </td>
   <td style="text-align:center;"> 0.073 </td>
   <td style="text-align:center;"> −1.665*** </td>
  </tr>
  <tr>
   <td style="text-align:left;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.231) </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.186) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Num.Obs. </td>
   <td style="text-align:center;"> 322 </td>
   <td style="text-align:center;"> 230 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 </td>
   <td style="text-align:center;"> 0.771 </td>
   <td style="text-align:center;"> 0.914 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 Adj. </td>
   <td style="text-align:center;"> 0.767 </td>
   <td style="text-align:center;"> 0.912 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> AIC </td>
   <td style="text-align:center;"> 1904.4 </td>
   <td style="text-align:center;"> 1165.4 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> BIC </td>
   <td style="text-align:center;"> 1930.8 </td>
   <td style="text-align:center;"> 1189.4 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Log.Lik. </td>
   <td style="text-align:center;"> −945.197 </td>
   <td style="text-align:center;"> −575.678 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> F </td>
   <td style="text-align:center;"> 212.917 </td>
   <td style="text-align:center;"> 477.709 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> RMSE </td>
   <td style="text-align:center;"> 4.56 </td>
   <td style="text-align:center;"> 2.96 </td>
  </tr>
</tbody>
<tfoot><tr><td style="padding: 0; " colspan="100%">
<sup></sup> + p &lt; 0.1, * p &lt; 0.05, ** p &lt; 0.01, *** p &lt; 0.001</td></tr></tfoot>
</table>

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-9-1.png" width="672" /><img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-9-2.png" width="672" />

Both models appear to have relatively high R^2 values, indicating higher levels of in-sample fit, but the model with data after 1996 appears to have a significantly higher R^2, reaching up to 0.91. Both models also have similar out-of-sample cross validation errors, centering around zero, but I find that the spread on the model with more data is slightly right skewed (meaning that the model is likely to underpredict Democrat performance). While this model also has a smaller range of prediction errors from 0, both seem to have a pretty substantial range.

However, there are several limitations of my model. For one, the state metrics that I use are easily confounded with other factors. For example, the amount of federal spending has not been found to indicate much without considering which party has provided that funding (5). Though I use aggregated funding since we do not have access to data following the 2020 election, it is an imperfect measure. Similarly, scholars have disagreed on what party benefits most from having higher overall turnout rates (9). Perhaps a next step may be to disaggregate turnout outcomes by party, available in our county turnout dataset. Additionally, on the note of turnout, the regression model including data as far back as 1984 includes many missing data points, because we do not have turnout metrics for many of these states in the 1980s/1990s in our datasets.

Nevertheless, I use these findings to predict outcomes in the seven states that numerous sources have declared as "battlegrounds" in the 2024 presidential election. (10)


Table: <span id="tab:unnamed-chunk-10"></span>Table 1: Prediction (Post 1984 Data)

|     State      | Predicted Winner | Democratic Vote Share |
|:--------------:|:----------------:|:---------------------:|
|    Arizona     |       DEM        |         53.97         |
|    Georgia     |       DEM        |         51.74         |
|    Michigan    |       DEM        |         53.37         |
|     Nevada     |       DEM        |         52.55         |
| North Carolina |       DEM        |         52.37         |
|  Pennsylvania  |       DEM        |         54.02         |
|   Wisconsin    |       DEM        |         53.32         |



Table: <span id="tab:unnamed-chunk-10"></span>Table 1: Prediction (Post 1996 Data)

|     State      | Predicted Winner | Democratic Vote Share |
|:--------------:|:----------------:|:---------------------:|
|    Arizona     |       DEM        |         56.20         |
|    Georgia     |       DEM        |         55.31         |
|    Michigan    |       DEM        |         56.94         |
|     Nevada     |       DEM        |         56.08         |
| North Carolina |       DEM        |         55.96         |
|  Pennsylvania  |       DEM        |         57.08         |
|   Wisconsin    |       DEM        |         57.28         |

Though these results appear promising for Vice President Harris, these predictions are more optimistic for her than I would expect them to be, given how close prominent forecasts predict the election to be (11). This is especially the case of the Post 1996 Data model. However, given that we found the post 1984 model to slightly skew towards underpredicting Democratic performance, this could lend more credence to the higher predictions found in the post-96 model. Regardless, I am looking forward to gathering feedback on these models and further improving them.

# References

St_transform, st_as_sf, tigris (shift_geometry), and ggpubr help pages

(1) Viridis color maps help page; Coord Map help page; Left Join; Data@Urban. 2018. “How to Create State and County Maps Easily in R.” Medium (blog). July 10, 2018. https://urban-institute.medium.com/how-to-create-state-and-county-maps-easily-in-r-577d29300bb2.
“R Append Data Frames - Spark By {Examples}.” n.d. Accessed October 21, 2024. https://sparkbyexamples.com/r-programming/r-append-dataframes/.; Julia. (2020, May 26). Answer to “Export R data to csv” [Online post]. Stack Overflow. https://stackoverflow.com/a/62017887; ialm. (2013, November 14). Answer to “How to save data file into .RData?” [Online post]. Stack Overflow. https://stackoverflow.com/a/19967638

(2) to_title_case help page, camille. 2022. “Answer to ‘Convert Column Names to Title Case.’” Stack Overflow. https://stackoverflow.com/a/70804865.
Khalilov, Murad. 2024. “Answer to ‘Rename All Columns to Title Case with {dplyr}.’” Stack Overflow. https://stackoverflow.com/a/78146810.
LurkerFinallyJoins. 2022. “Adding Value to End of Every Value in R Column.” Reddit Post. R/Rlanguage. www.reddit.com/r/Rlanguage/comments/sh9rbu/adding_value_to_end_of_every_value_in_r_column/. Holtz, Yan. n.d. “Dual Y Axis with R and Ggplot2.” Accessed October 21, 2024. https://www.r-graph-gallery.com/line-chart-dual-Y-axis-ggplot2.html.; “Reorder the Column of Dataframe in R Using Dplyr.” 2021. GeeksforGeeks. September 1, 2021. https://www.geeksforgeeks.org/reorder-the-column-of-dataframe-in-r-using-dplyr/.


(3) Andina, Matias. 2016. “Answer to ‘How to Remove $ and % from Columns in R?’” Stack Overflow. https://stackoverflow.com/a/35757945.

(4) Darr, Joshua P., and Matthew S. Levendusky. 2014. “Relying on the Ground Game: The Placement and Effect of Campaign Field Offices.” American Politics Research 42 (3): 529–48. https://doi.org/10.1177/1532673X13500520.

(5) Kalla, Joshua L., and David E. Broockman. 2018. “The Minimal Persuasive Effects of Campaign Contact in General Elections: Evidence from 49 Field Experiments.” American Political Science Review 112 (1): 148–66. https://doi.org/10.1017/S0003055417000363.

(6) Kriner, Douglas L., and Andrew Reeves. 2012. “The Influence of Federal Spending on Presidential Elections.” American Political Science Review 106 (2): 348–66. https://doi.org/10.1017/S0003055412000159.

(7) Students of History. “The Great Switch: How Republicans and Democrats Flipped Ideologies.” Accessed September 7, 2024. https://www.studentsofhistory.com/ideologies-flip-Democratic-Republican-parties.; U.S. Embassy & Consulate in the Kingdom of Denmark. “Presidential Elections and the American Political System.” Accessed September 7, 2024. https://dk.usembassy.gov/usa-i-skolen/presidential-elections-and-the-american-political-system/. (As cited in my first blog post); “Presidential Election of 1984 - 270toWin.” n.d. 270toWin.Com. Accessed October 23, 2024. https://www.270towin.com/1984_Election/.

(8) If_else help page; Bobbitt, Zach. 2021. “How to Sort Values Alphabetically in R.” Statology. July 13, 2021. https://www.statology.org/sort-alphabetically-in-r/.
———. 2022. “How to Calculate Lagged Values in R (With Examples).” Statology. December 13, 2022. https://www.statology.org/r-lag/.

(9) Shaw, Daron R., and John R. Petrocik. 2020. The Turnout Myth: Voting Rates and Partisan Outcomes in American National Elections. Oxford University Press.

(10) Boyce, Lily, Lazaro Gamio, Eli Murray, and Alicia Parlapiano. 2024. “Tracking the Swing States for Harris and Trump.” The New York Times, August 14, 2024, sec. U.S. https://www.nytimes.com/interactive/2024/us/elections/presidential-election-swing-states.html.
Davis Jr., Elliott. n.d. “7 States That Could Sway the 2024 Presidential Election.” US News & World Report. Accessed October 22, 2024. //www.usnews.com/news/elections/articles/7-swing-states-that-could-decide-the-2024-presidential-election.
Perry, Kati, Dan Keating, and Aaron Blake. 2024. “A Guide to the 7 Battleground States That Could Swing the Election.” Washington Post. October 21, 2024. https://www.washingtonpost.com/elections/interactive/2024/2024-swing-states-trump-harris/.
Vox Staff. 2024. “The 7 States That Will Decide the 2024 Election.” Vox. October 21, 2024. https://www.vox.com/today-explained-podcast/378112/battleground-states-election-2024-trump-harris.

(11) Morris, G. Elliott. 2024. “Who Is Favored To Win The 2024 Presidential Election?” FiveThirtyEight. June 11, 2024. https://projects.fivethirtyeight.com/2024-election-forecast/.


# Data Sources
All Data Sources are provided by GOV 1372 Staff

Popular Vote Datasets

- National Popular Vote Data from Wikipedia, Abramowitz (2020), Abramowitz (2020) replication data, and manual changes

- State Popular Vote Data from MIT elections project, Wikipedia, and manual editing

Economic Data

- FRED Data from St. Louis FRED

- Grants Data from Kriner and Reeves (2015) replication data

Polling Data

- State Polls from FiveThirtyEight poll averages and preprocessing


Data sources for state and county-level turnout, campaign event locations, and sites of field offices are unclear, but were generously provided by the GOV 1372 course staff

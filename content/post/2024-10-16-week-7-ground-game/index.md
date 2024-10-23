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



For this analysis, I am interested in exploring the relationship between ground-campaign events and voter turnout. Given that ground campaigns often happen on a relatively local level, I focus on my home state of Michigan for my analysis this week, reviewing how the prevalence of field offices and campaign events relative to the region's population in 2016 impacted turnout outcomes in prior elections.

First, I visualized the relationship between field offices/campaign events and county turnout as a percentage of the area's population. The first map below indicates the location of field offices (+) and campaign events (∆) associated with each party. The second, put together using a mapping tool developed by the Urban Institute and generously described on their Medium site (1), indicates voter turnout in each county in Michigan. Unfortunately, we do not appear to have county-level turnout data for the 2016 election, so I use 2020 county-level turnout instead. While this is an imperfect metric, especially because of the effects of the COVID-19 pandemic, exploring this relationship could also potentially suggest if there are any long-term effects of the location of a campaign office in a region on future political cycles, or if the effects largely wean as the candidate changes.


```
## 
  |                                                                            
  |                                                                      |   0%
  |                                                                            
  |                                                                      |   1%
  |                                                                            
  |=                                                                     |   1%
  |                                                                            
  |=                                                                     |   2%
  |                                                                            
  |==                                                                    |   2%
  |                                                                            
  |==                                                                    |   3%
  |                                                                            
  |==                                                                    |   4%
  |                                                                            
  |===                                                                   |   4%
  |                                                                            
  |===                                                                   |   5%
  |                                                                            
  |====                                                                  |   5%
  |                                                                            
  |====                                                                  |   6%
  |                                                                            
  |=====                                                                 |   6%
  |                                                                            
  |=====                                                                 |   7%
  |                                                                            
  |=====                                                                 |   8%
  |                                                                            
  |======                                                                |   8%
  |                                                                            
  |======                                                                |   9%
  |                                                                            
  |=======                                                               |   9%
  |                                                                            
  |=======                                                               |  10%
  |                                                                            
  |=======                                                               |  11%
  |                                                                            
  |========                                                              |  11%
  |                                                                            
  |========                                                              |  12%
  |                                                                            
  |=========                                                             |  12%
  |                                                                            
  |=========                                                             |  13%
  |                                                                            
  |==========                                                            |  14%
  |                                                                            
  |==========                                                            |  15%
  |                                                                            
  |===========                                                           |  15%
  |                                                                            
  |===========                                                           |  16%
  |                                                                            
  |============                                                          |  17%
  |                                                                            
  |============                                                          |  18%
  |                                                                            
  |=============                                                         |  18%
  |                                                                            
  |=============                                                         |  19%
  |                                                                            
  |==============                                                        |  19%
  |                                                                            
  |==============                                                        |  20%
  |                                                                            
  |==============                                                        |  21%
  |                                                                            
  |===============                                                       |  21%
  |                                                                            
  |===============                                                       |  22%
  |                                                                            
  |================                                                      |  22%
  |                                                                            
  |================                                                      |  23%
  |                                                                            
  |================                                                      |  24%
  |                                                                            
  |=================                                                     |  24%
  |                                                                            
  |=================                                                     |  25%
  |                                                                            
  |==================                                                    |  25%
  |                                                                            
  |==================                                                    |  26%
  |                                                                            
  |===================                                                   |  26%
  |                                                                            
  |===================                                                   |  27%
  |                                                                            
  |===================                                                   |  28%
  |                                                                            
  |====================                                                  |  28%
  |                                                                            
  |====================                                                  |  29%
  |                                                                            
  |=====================                                                 |  29%
  |                                                                            
  |=====================                                                 |  30%
  |                                                                            
  |=====================                                                 |  31%
  |                                                                            
  |======================                                                |  31%
  |                                                                            
  |======================                                                |  32%
  |                                                                            
  |=======================                                               |  32%
  |                                                                            
  |=======================                                               |  33%
  |                                                                            
  |=======================                                               |  34%
  |                                                                            
  |========================                                              |  34%
  |                                                                            
  |========================                                              |  35%
  |                                                                            
  |=========================                                             |  35%
  |                                                                            
  |=========================                                             |  36%
  |                                                                            
  |==========================                                            |  36%
  |                                                                            
  |==========================                                            |  37%
  |                                                                            
  |==========================                                            |  38%
  |                                                                            
  |===========================                                           |  38%
  |                                                                            
  |===========================                                           |  39%
  |                                                                            
  |============================                                          |  39%
  |                                                                            
  |============================                                          |  40%
  |                                                                            
  |============================                                          |  41%
  |                                                                            
  |=============================                                         |  41%
  |                                                                            
  |=============================                                         |  42%
  |                                                                            
  |==============================                                        |  42%
  |                                                                            
  |==============================                                        |  43%
  |                                                                            
  |===============================                                       |  44%
  |                                                                            
  |===============================                                       |  45%
  |                                                                            
  |================================                                      |  45%
  |                                                                            
  |================================                                      |  46%
  |                                                                            
  |=================================                                     |  47%
  |                                                                            
  |=================================                                     |  48%
  |                                                                            
  |==================================                                    |  48%
  |                                                                            
  |==================================                                    |  49%
  |                                                                            
  |===================================                                   |  49%
  |                                                                            
  |===================================                                   |  50%
  |                                                                            
  |===================================                                   |  51%
  |                                                                            
  |====================================                                  |  51%
  |                                                                            
  |====================================                                  |  52%
  |                                                                            
  |=====================================                                 |  52%
  |                                                                            
  |=====================================                                 |  53%
  |                                                                            
  |=====================================                                 |  54%
  |                                                                            
  |======================================                                |  54%
  |                                                                            
  |======================================                                |  55%
  |                                                                            
  |=======================================                               |  55%
  |                                                                            
  |=======================================                               |  56%
  |                                                                            
  |========================================                              |  56%
  |                                                                            
  |========================================                              |  57%
  |                                                                            
  |========================================                              |  58%
  |                                                                            
  |=========================================                             |  58%
  |                                                                            
  |=========================================                             |  59%
  |                                                                            
  |==========================================                            |  59%
  |                                                                            
  |==========================================                            |  60%
  |                                                                            
  |==========================================                            |  61%
  |                                                                            
  |===========================================                           |  61%
  |                                                                            
  |===========================================                           |  62%
  |                                                                            
  |============================================                          |  62%
  |                                                                            
  |============================================                          |  63%
  |                                                                            
  |============================================                          |  64%
  |                                                                            
  |=============================================                         |  64%
  |                                                                            
  |=============================================                         |  65%
  |                                                                            
  |==============================================                        |  65%
  |                                                                            
  |==============================================                        |  66%
  |                                                                            
  |===============================================                       |  66%
  |                                                                            
  |===============================================                       |  67%
  |                                                                            
  |===============================================                       |  68%
  |                                                                            
  |================================================                      |  68%
  |                                                                            
  |================================================                      |  69%
  |                                                                            
  |=================================================                     |  69%
  |                                                                            
  |=================================================                     |  70%
  |                                                                            
  |=================================================                     |  71%
  |                                                                            
  |==================================================                    |  71%
  |                                                                            
  |==================================================                    |  72%
  |                                                                            
  |===================================================                   |  72%
  |                                                                            
  |===================================================                   |  73%
  |                                                                            
  |====================================================                  |  74%
  |                                                                            
  |====================================================                  |  75%
  |                                                                            
  |=====================================================                 |  75%
  |                                                                            
  |=====================================================                 |  76%
  |                                                                            
  |======================================================                |  77%
  |                                                                            
  |======================================================                |  78%
  |                                                                            
  |=======================================================               |  78%
  |                                                                            
  |=======================================================               |  79%
  |                                                                            
  |========================================================              |  79%
  |                                                                            
  |========================================================              |  80%
  |                                                                            
  |========================================================              |  81%
  |                                                                            
  |=========================================================             |  81%
  |                                                                            
  |=========================================================             |  82%
  |                                                                            
  |==========================================================            |  82%
  |                                                                            
  |==========================================================            |  83%
  |                                                                            
  |==========================================================            |  84%
  |                                                                            
  |===========================================================           |  84%
  |                                                                            
  |===========================================================           |  85%
  |                                                                            
  |============================================================          |  85%
  |                                                                            
  |============================================================          |  86%
  |                                                                            
  |=============================================================         |  87%
  |                                                                            
  |=============================================================         |  88%
  |                                                                            
  |==============================================================        |  88%
  |                                                                            
  |==============================================================        |  89%
  |                                                                            
  |===============================================================       |  89%
  |                                                                            
  |===============================================================       |  90%
  |                                                                            
  |===============================================================       |  91%
  |                                                                            
  |================================================================      |  91%
  |                                                                            
  |================================================================      |  92%
  |                                                                            
  |=================================================================     |  92%
  |                                                                            
  |=================================================================     |  93%
  |                                                                            
  |=================================================================     |  94%
  |                                                                            
  |==================================================================    |  94%
  |                                                                            
  |==================================================================    |  95%
  |                                                                            
  |===================================================================   |  95%
  |                                                                            
  |===================================================================   |  96%
  |                                                                            
  |====================================================================  |  97%
  |                                                                            
  |====================================================================  |  98%
  |                                                                            
  |===================================================================== |  98%
  |                                                                            
  |===================================================================== |  99%
  |                                                                            
  |======================================================================|  99%
  |                                                                            
  |======================================================================| 100%
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />

From observing these maps, it does not appear that there is a substantial relationship between the location of 2016 Campaign Activity and 2020 turnout. In fact, if we look at the southeastern part of the state, where much election activity by both parties was concentrated, we see that there was relatively low electoral turnout. However, it is also important to recognize that these activities were likely clustered around the city of Detroit, where a substantial part of Michigan's population lives. Therefore, even if turnout is low, there still could have been a significant number of voters. In other parts of the state, the relationship seems relatively unclear from just this visual representation. Therefore, we also trained a simple linear regression model of the relationship between campaign activities and turnout at the national level. While we have turnout metrics at the county level for 2020, we unfortunately do not have campaign activities measured by county, which is why I regress these two metrics at the national level.



```
## 
## Call:
## lm(formula = vep_turnout ~ n_ev_D + ev_diff_D_R + n_office_D + 
##     office_diff_D_R, data = d_campaign_events_vote)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -10.729  -2.986   1.052   3.327   9.145 
## 
## Coefficients:
##                 Estimate Std. Error t value Pr(>|t|)    
## (Intercept)     61.53278    1.27384  48.305   <2e-16 ***
## n_ev_D          -0.35394    0.24916  -1.421    0.169    
## ev_diff_D_R      0.01492    0.36880   0.040    0.968    
## n_office_D       0.05022    0.22609   0.222    0.826    
## office_diff_D_R  0.28757    0.22023   1.306    0.205    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 5.174 on 22 degrees of freedom
##   (8 observations deleted due to missingness)
## Multiple R-squared:  0.3488,	Adjusted R-squared:  0.2304 
## F-statistic: 2.946 on 4 and 22 DF,  p-value: 0.04319
```

```
## 
## Call:
## lm(formula = vep_turnout ~ n_ev_R + ev_diff_R_D + n_office_R + 
##     office_diff_R_D, data = d_campaign_events_vote)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -10.729  -2.986   1.052   3.327   9.145 
## 
## Coefficients:
##                 Estimate Std. Error t value Pr(>|t|)    
## (Intercept)     61.53278    1.27384  48.305   <2e-16 ***
## n_ev_R          -0.35394    0.24916  -1.421   0.1695    
## ev_diff_R_D      0.33903    0.26164   1.296   0.2085    
## n_office_R       0.05022    0.22609   0.222   0.8262    
## office_diff_R_D -0.33780    0.13655  -2.474   0.0216 *  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 5.174 on 22 degrees of freedom
##   (8 observations deleted due to missingness)
## Multiple R-squared:  0.3488,	Adjusted R-squared:  0.2304 
## F-statistic: 2.946 on 4 and 22 DF,  p-value: 0.04319
```

```
## 
## Call:
## lm(formula = vep_turnout ~ total_events + total_offices, data = d_campaign_events_vote)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -10.0306  -3.5256  -0.8565   3.8785  11.0022 
## 
## Coefficients:
##               Estimate Std. Error t value Pr(>|t|)    
## (Intercept)   61.84217    1.31385  47.069   <2e-16 ***
## total_events  -0.16651    0.11596  -1.436   0.1639    
## total_offices  0.18116    0.08353   2.169   0.0402 *  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 5.507 on 24 degrees of freedom
##   (8 observations deleted due to missingness)
## Multiple R-squared:  0.1952,	Adjusted R-squared:  0.1281 
## F-statistic: 2.911 on 2 and 24 DF,  p-value: 0.07383
```

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

This regression confirms my previous assumptions -- metrics of campaign activity alone largely do not appear to have a significant effect on turnout. However, one important exception to this is the number of total offices driving overall turnout in a statistically significant manner. This latter result seems to align with Darr and Levendusky's findings that field offices increase turnout (3). However, it is interesting to note that campaign events, unintuitively, appear to decrease turnout


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

Once again, none of these results appear particularly significant, although we find a positive relationship between total events and turnout in this model (though this variable is not significant in either). This may lend credence to Kalla and Broockman's 2018 work, which highlights that ground campaigns have a relatively minimal effect on outcomes (4).

Following this analysis, I also began building my own predictive model of electoral outcomes, based on my findings from previous weeks. Through an initial conversation with Matt Dardet, I was inspired to start with a relatively parsimonious model -- Alan Abramowitz's Time for Change Model. While I still use some parts of this model, including its incorporation of GDP growth and incumbency status, I wanted to build a model that was generalizable to candidates who were not incumbents. Given that our analyses from previous weeks also indicated that metrics like turnout, polling, and federal grant spending (as discussed by Kriner and Reeves (5)) appeared significant, I included these metrics as well. I also notably excluded metrics related to campaign activities, given the rather insignificant results that I found when incorporating them this week and last. 

My linear regression model considers GDP growth in the quarter immediately prior to the election (although I use 2nd quarter data when predicting 2024 outcomes since it is the most recent data we have available), unemployment, and candidate incumbency at the national level and poll support five weeks prior to the election, total federal grant funding allocation since 2000, and turnout in the last presidential election at the state level. Using this model, I aim to predict two-party Democratic vote share. Then, I impute Republican vote share by subtracting the Democratic two-party vote share from 100.  Importantly, I also only used data after 1996, wanting to avoid biasing my findings with results from a time when the American political landscape was significantly different than it is today (6).




<table style="NAborder-bottom: 0; width: auto !important; margin-left: auto; margin-right: auto;" class="table">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:center;"> &amp;nbsp;Predicted Democratic Vote Share </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:center;"> 8.083*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (1.980) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> GDP_growth_quarterly </td>
   <td style="text-align:center;"> −0.426*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.048) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> mean_5_wk_poll_support </td>
   <td style="text-align:center;"> 1.162*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.032) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> incumbent </td>
   <td style="text-align:center;"> 2.798*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.702) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> total_grant_since_2000 </td>
   <td style="text-align:center;"> 0.000+ </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.000) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> lastpresturnout </td>
   <td style="text-align:center;"> 0.044 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.031) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> unemployment </td>
   <td style="text-align:center;"> −2.248*** </td>
  </tr>
  <tr>
   <td style="text-align:left;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.232) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Num.Obs. </td>
   <td style="text-align:center;"> 230 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 </td>
   <td style="text-align:center;"> 0.920 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 Adj. </td>
   <td style="text-align:center;"> 0.918 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> AIC </td>
   <td style="text-align:center;"> 1151.5 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> BIC </td>
   <td style="text-align:center;"> 1179.0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Log.Lik. </td>
   <td style="text-align:center;"> −567.769 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> F </td>
   <td style="text-align:center;"> 427.175 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> RMSE </td>
   <td style="text-align:center;"> 2.86 </td>
  </tr>
</tbody>
<tfoot><tr><td style="padding: 0; " colspan="100%">
<sup></sup> + p &lt; 0.1, * p &lt; 0.05, ** p &lt; 0.01, *** p &lt; 0.001</td></tr></tfoot>
</table>

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-9-1.png" width="672" />

This model appears to have a very high r^2 of 0.92, indicating that the OLS coefficients seemed to have a high in-sample prediction ability. However, the results appeared less promising when testing out-of-sample errors via cross-validation, with some errors actually being higher than the difference between the actual minimum and maximum value of democratic vote share that a state could have. This may be due to several limitations of my model. For one, the state metrics that I use are easily confounded with other factors. For example, the amount of federal spending has not been found to indicate much without considering which party has provided that funding. Though I use post-2000 funding to provide an aggregate since we do not have access to data following the 2020 election, it is an imperfect measure. Similarly, scholars have disagreed on what party benefits most from having higher overall turnout rates (8).

Nevertheless, I use these findings to predict outcomes in the seven states that numerous sources have declared as "battlegrounds" in the 2024 presidential election. (9)


|     State      | Predicted Winner |
|:--------------:|:----------------:|
|    Arizona     |       DEM        |
|    Georgia     |       DEM        |
|    Michigan    |       DEM        |
|     Nevada     |       DEM        |
| North Carolina |       DEM        |
|  Pennsylvania  |       DEM        |
|   Wisconsin    |       DEM        |

Though these results appear promising for Vice President Harris, I hope to continue to improve this model to provide a more accurate metric.

# References

St_transform, tigris (shift_geometry), and ggpubr help pages

(1) Viridis color maps help page; Coord Map help page; Left Join; Data@Urban. 2018. “How to Create State and County Maps Easily in R.” Medium (blog). July 10, 2018. https://urban-institute.medium.com/how-to-create-state-and-county-maps-easily-in-r-577d29300bb2.
“R Append Data Frames - Spark By {Examples}.” n.d. Accessed October 21, 2024. https://sparkbyexamples.com/r-programming/r-append-dataframes/.

(2) to_title_case help page, camille. 2022. “Answer to ‘Convert Column Names to Title Case.’” Stack Overflow. https://stackoverflow.com/a/70804865.
Khalilov, Murad. 2024. “Answer to ‘Rename All Columns to Title Case with {dplyr}.’” Stack Overflow. https://stackoverflow.com/a/78146810.
LurkerFinallyJoins. 2022. “Adding Value to End of Every Value in R Column.” Reddit Post. R/Rlanguage. www.reddit.com/r/Rlanguage/comments/sh9rbu/adding_value_to_end_of_every_value_in_r_column/. Holtz, Yan. n.d. “Dual Y Axis with R and Ggplot2.” Accessed October 21, 2024. https://www.r-graph-gallery.com/line-chart-dual-Y-axis-ggplot2.html.

(3) Darr, Joshua P., and Matthew S. Levendusky. 2014. “Relying on the Ground Game: The Placement and Effect of Campaign Field Offices.” American Politics Research 42 (3): 529–48. https://doi.org/10.1177/1532673X13500520.

(4) Kalla, Joshua L., and David E. Broockman. 2018. “The Minimal Persuasive Effects of Campaign Contact in General Elections: Evidence from 49 Field Experiments.” American Political Science Review 112 (1): 148–66. https://doi.org/10.1017/S0003055417000363.

(5) Kriner, Douglas L., and Andrew Reeves. 2012. “The Influence of Federal Spending on Presidential Elections.” American Political Science Review 106 (2): 348–66. https://doi.org/10.1017/S0003055412000159.

(6) Students of History. “The Great Switch: How Republicans and Democrats Flipped Ideologies.” Accessed September 7, 2024. https://www.studentsofhistory.com/ideologies-flip-Democratic-Republican-parties.; U.S. Embassy & Consulate in the Kingdom of Denmark. “Presidential Elections and the American Political System.” Accessed September 7, 2024. https://dk.usembassy.gov/usa-i-skolen/presidential-elections-and-the-american-political-system/. (As cited in my first blog post)

(7) If_else help page

(8) Shaw, Daron R., and John R. Petrocik. 2020. The Turnout Myth: Voting Rates and Partisan Outcomes in American National Elections. Oxford University Press.

(9) Boyce, Lily, Lazaro Gamio, Eli Murray, and Alicia Parlapiano. 2024. “Tracking the Swing States for Harris and Trump.” The New York Times, August 14, 2024, sec. U.S. https://www.nytimes.com/interactive/2024/us/elections/presidential-election-swing-states.html.
Davis Jr., Elliott. n.d. “7 States That Could Sway the 2024 Presidential Election.” US News & World Report. Accessed October 22, 2024. //www.usnews.com/news/elections/articles/7-swing-states-that-could-decide-the-2024-presidential-election.
Perry, Kati, Dan Keating, and Aaron Blake. 2024. “A Guide to the 7 Battleground States That Could Swing the Election.” Washington Post. October 21, 2024. https://www.washingtonpost.com/elections/interactive/2024/2024-swing-states-trump-harris/.
Vox Staff. 2024. “The 7 States That Will Decide the 2024 Election.” Vox. October 21, 2024. https://www.vox.com/today-explained-podcast/378112/battleground-states-election-2024-trump-harris.

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

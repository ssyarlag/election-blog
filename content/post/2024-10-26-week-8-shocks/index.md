---
title: Week 8 - Shocks
author: Shriya Yarlagadda
date: '2024-10-26'
slug: week-8-shocks
categories: []
tags: []
---
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />

Although we discussed the impacts of electoral shocks in class this week, my blog post this week will focus on refining my model from last week. As I did last week, I will continue to compare two models, one using data from after 1984 and the other using data from after 1996.







I planned to make three initial changes this week. First, upon the recommendation of Matt Dardet, I took the log of grant allocation in order to see if my model predicted a significant effect. Second, after being inspired by my classmate Alex Heuss, I decided to measure the outcome of Democratic vote share, rather than two-party vote share, in order to better account for the disruptive ability of third-party candidates. Finally, I added confidence intervals to my measures, seeking to better estimate the precision of my predictions.

## Update 1: Grant Allocation + Single Party Vote Share + Confidence Intervals

<table style="NAborder-bottom: 0; width: auto !important; margin-left: auto; margin-right: auto;" class="table">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:center;"> &amp;nbsp;Post 84 </th>
   <th style="text-align:center;"> &amp;nbsp;Post 96 </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:center;"> −2.390 </td>
   <td style="text-align:center;"> −0.836 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (2.434) </td>
   <td style="text-align:center;"> (2.173) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> GDP_growth_quarterly </td>
   <td style="text-align:center;"> −0.327*** </td>
   <td style="text-align:center;"> −0.356*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.044) </td>
   <td style="text-align:center;"> (0.039) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> mean_5_wk_poll_support </td>
   <td style="text-align:center;"> 0.962*** </td>
   <td style="text-align:center;"> 1.092*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.030) </td>
   <td style="text-align:center;"> (0.031) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> turnout_lag1 </td>
   <td style="text-align:center;"> 0.008 </td>
   <td style="text-align:center;"> 0.019 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.029) </td>
   <td style="text-align:center;"> (0.027) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> unemployment </td>
   <td style="text-align:center;"> −0.576*** </td>
   <td style="text-align:center;"> −0.979*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.159) </td>
   <td style="text-align:center;"> (0.156) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> log(total_grant) </td>
   <td style="text-align:center;"> 1.353*** </td>
   <td style="text-align:center;"> 0.694** </td>
  </tr>
  <tr>
   <td style="text-align:left;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.229) </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.243) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Num.Obs. </td>
   <td style="text-align:center;"> 322 </td>
   <td style="text-align:center;"> 230 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 </td>
   <td style="text-align:center;"> 0.885 </td>
   <td style="text-align:center;"> 0.937 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 Adj. </td>
   <td style="text-align:center;"> 0.883 </td>
   <td style="text-align:center;"> 0.935 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> AIC </td>
   <td style="text-align:center;"> 1666.9 </td>
   <td style="text-align:center;"> 1083.0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> BIC </td>
   <td style="text-align:center;"> 1693.3 </td>
   <td style="text-align:center;"> 1107.0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Log.Lik. </td>
   <td style="text-align:center;"> −826.442 </td>
   <td style="text-align:center;"> −534.485 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> F </td>
   <td style="text-align:center;"> 485.880 </td>
   <td style="text-align:center;"> 661.851 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> RMSE </td>
   <td style="text-align:center;"> 3.15 </td>
   <td style="text-align:center;"> 2.47 </td>
  </tr>
</tbody>
<tfoot><tr><td style="padding: 0; " colspan="100%">
<sup></sup> + p &lt; 0.1, * p &lt; 0.05, ** p &lt; 0.01, *** p &lt; 0.001</td></tr></tfoot>
</table>

Post 1984 Model:


|     State      | Predicted Winner | Democratic Vote Share | Low Pred | High Pred |
|:--------------:|:----------------:|:---------------------:|:--------:|:---------:|
|    Arizona     |       DEM        |         52.22         |  51.17   |   53.26   |
|    Georgia     |       DEM        |         50.06         |  49.10   |   51.02   |
|    Michigan    |       DEM        |         52.23         |  51.13   |   53.34   |
|     Nevada     |       DEM        |         51.33         |  50.47   |   52.19   |
| North Carolina |       DEM        |         51.05         |  49.99   |   52.11   |
|  Pennsylvania  |       DEM        |         52.80         |  51.79   |   53.82   |
|   Wisconsin    |       DEM        |         51.98         |  50.81   |   53.16   |

Post 1996 Model:


|     State      | Predicted Winner | Democratic Vote Share | Low Pred | High Pred |
|:--------------:|:----------------:|:---------------------:|:--------:|:---------:|
|    Arizona     |       DEM        |         52.87         |  51.77   |   53.97   |
|    Georgia     |       DEM        |         52.02         |  51.11   |   52.93   |
|    Michigan    |       DEM        |         53.72         |  52.63   |   54.82   |
|     Nevada     |       DEM        |         53.01         |  52.19   |   53.83   |
| North Carolina |       DEM        |         52.72         |  51.68   |   53.76   |
|  Pennsylvania  |       DEM        |         53.90         |  52.86   |   54.94   |
|   Wisconsin    |       DEM        |         53.88         |  52.73   |   55.04   |

By taking the log of grant allocation, we find a highly significant prediction value in the ultimate outcome. Furthermore, although the models still overwhelmingly appear to predict that the Democrats will win all of the battleground states, which seems relatively unlikely, these models show additional uncertainty, with the values for both Georgia and North Carolina falling within a range of uncertainty. To get an additional benchmark for the performance of both of these models, I also run out-of-sample cross validation

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-7-1.png" width="672" /><img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-7-2.png" width="672" />

Though these results are slightly right skewed, we find a relatively small range of out-of-sample errors, especially for the post 84 model, and a high clustering around 0! This suggests that the post 84, especially, may be a strong predictor of out-of-sample outcomes.

To further improve my model, I was interested in including several additional metrics that we currently have access to, namely 1) Democratic vote share in the last election 2) Democratic vote share in the second-last election. I anticipated that these metrics will add an estimation baseline to the predictions

## Update 2: Adding Democratic Vote Share in Last Two Elections

<table style="NAborder-bottom: 0; width: auto !important; margin-left: auto; margin-right: auto;" class="table">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:center;"> &amp;nbsp;Post 84 </th>
   <th style="text-align:center;"> &amp;nbsp;Post 96 </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:center;"> −3.550+ </td>
   <td style="text-align:center;"> −1.680 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (2.101) </td>
   <td style="text-align:center;"> (1.885) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> GDP_growth_quarterly </td>
   <td style="text-align:center;"> −0.271*** </td>
   <td style="text-align:center;"> −0.348*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.038) </td>
   <td style="text-align:center;"> (0.035) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> mean_5_wk_poll_support </td>
   <td style="text-align:center;"> 0.744*** </td>
   <td style="text-align:center;"> 0.843*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.034) </td>
   <td style="text-align:center;"> (0.039) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> turnout_lag1 </td>
   <td style="text-align:center;"> 0.008 </td>
   <td style="text-align:center;"> −0.006 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.025) </td>
   <td style="text-align:center;"> (0.024) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> unemployment </td>
   <td style="text-align:center;"> −0.477*** </td>
   <td style="text-align:center;"> −0.562*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.139) </td>
   <td style="text-align:center;"> (0.144) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> log(total_grant) </td>
   <td style="text-align:center;"> 0.883*** </td>
   <td style="text-align:center;"> 0.290 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.202) </td>
   <td style="text-align:center;"> (0.215) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> D_pv_lag1 </td>
   <td style="text-align:center;"> 0.261*** </td>
   <td style="text-align:center;"> 0.241*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.035) </td>
   <td style="text-align:center;"> (0.037) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> D_pv_lag2 </td>
   <td style="text-align:center;"> 0.040 </td>
   <td style="text-align:center;"> 0.052 </td>
  </tr>
  <tr>
   <td style="text-align:left;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.033) </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.033) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Num.Obs. </td>
   <td style="text-align:center;"> 322 </td>
   <td style="text-align:center;"> 230 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 </td>
   <td style="text-align:center;"> 0.915 </td>
   <td style="text-align:center;"> 0.953 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 Adj. </td>
   <td style="text-align:center;"> 0.913 </td>
   <td style="text-align:center;"> 0.951 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> AIC </td>
   <td style="text-align:center;"> 1572.2 </td>
   <td style="text-align:center;"> 1018.8 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> BIC </td>
   <td style="text-align:center;"> 1606.2 </td>
   <td style="text-align:center;"> 1049.8 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Log.Lik. </td>
   <td style="text-align:center;"> −777.103 </td>
   <td style="text-align:center;"> −500.417 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> F </td>
   <td style="text-align:center;"> 484.614 </td>
   <td style="text-align:center;"> 641.010 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> RMSE </td>
   <td style="text-align:center;"> 2.70 </td>
   <td style="text-align:center;"> 2.13 </td>
  </tr>
</tbody>
<tfoot><tr><td style="padding: 0; " colspan="100%">
<sup></sup> + p &lt; 0.1, * p &lt; 0.05, ** p &lt; 0.01, *** p &lt; 0.001</td></tr></tfoot>
</table>

When adding in these variables, we interestingly find that the R\^2 value of both models is still incredibly high, suggesting that these models have high in-sample prediction ability. To see how well these models perform on out-of-sample data, I again conduct model cross-validation.

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-9-1.png" width="672" /><img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-9-2.png" width="672" />

Unfortunately, it appears that these models are still left-skewed, but have more values that appear further away from zero. In particular, it appears that these models are underpredicting Democratic vote share relative to the actual outcome. For reference, I also wanted to test how this would translate to 2024 prediction outcomes.



Post 1984 Model:


|     State      | Predicted Winner | Democratic Vote Share | Low Pred | High Pred |
|:--------------:|:----------------:|:---------------------:|:--------:|:---------:|
|    Arizona     |       DEM        |         51.84         |  50.89   |   52.79   |
|    Georgia     |       DEM        |         50.53         |  49.63   |   51.42   |
|    Michigan    |       DEM        |         52.43         |  51.43   |   53.42   |
|     Nevada     |       DEM        |         51.67         |  50.90   |   52.44   |
| North Carolina |       DEM        |         51.00         |  50.05   |   51.95   |
|  Pennsylvania  |       DEM        |         52.64         |  51.74   |   53.54   |
|   Wisconsin    |       DEM        |         51.98         |  50.93   |   53.04   |

Post 1996 Model:


|     State      | Predicted Winner | Democratic Vote Share | Low Pred | High Pred |
|:--------------:|:----------------:|:---------------------:|:--------:|:---------:|
|    Arizona     |       DEM        |         50.96         |  49.88   |   52.04   |
|    Georgia     |       DEM        |         50.83         |  49.97   |   51.69   |
|    Michigan    |       DEM        |         52.16         |  51.13   |   53.20   |
|     Nevada     |       DEM        |         51.78         |  51.01   |   52.54   |
| North Carolina |       DEM        |         50.96         |  49.96   |   51.96   |
|  Pennsylvania  |       DEM        |         52.13         |  51.13   |   53.12   |
|   Wisconsin    |       DEM        |         52.05         |  50.95   |   53.15   |

Despite this greater skew, we do not see a substantive shift in outcomes, with a Democratic sweep still being predicted. However, it is interesting to note that the post 96 model appears to predict a more conservative Democratic vote share given these specifications, with the Arizona, Georgia, and North Carolina models all predicting uncertain outcomes.

Given that changing the variables included in my models does not seem to have a clear and direct effect on our prediction outcomes, I considered updating their form. To inform this decision, I plotted the relationship between Democratic turnout and each of the explanatory models that I had included in my prediction, aside from federal funding allocation.

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-13-1.png" width="672" />

From these graphs, we can confirm that lagged vote share from the prior two elections and mean poll support are strongly linearly related to our predicted outcome. This suggests that a it might not be necessary to alter the functional form of these variables in our model. However, it appears that the impact of GDP growth, unemployment rate, and turnout in the last election have a rather ambiguous effect.

Out of curiosity, I wanted to how much the results would vary if I only included the three highly predictive variables identified here in my prediction models. I run this analysis below.

## Update 3: Only Poll Support and Vote Share in Last Two Elections

<table style="NAborder-bottom: 0; width: auto !important; margin-left: auto; margin-right: auto;" class="table">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:center;"> &amp;nbsp;Post 84 </th>
   <th style="text-align:center;"> &amp;nbsp;Post 96 </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:center;"> −2.185* </td>
   <td style="text-align:center;"> −3.538*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.889) </td>
   <td style="text-align:center;"> (0.883) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> mean_5_wk_poll_support </td>
   <td style="text-align:center;"> 0.745*** </td>
   <td style="text-align:center;"> 0.820*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.030) </td>
   <td style="text-align:center;"> (0.035) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> D_pv_lag1 </td>
   <td style="text-align:center;"> 0.324*** </td>
   <td style="text-align:center;"> 0.358*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.032) </td>
   <td style="text-align:center;"> (0.037) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> D_pv_lag2 </td>
   <td style="text-align:center;"> 0.036 </td>
   <td style="text-align:center;"> −0.044 </td>
  </tr>
  <tr>
   <td style="text-align:left;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.031) </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.035) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Num.Obs. </td>
   <td style="text-align:center;"> 434 </td>
   <td style="text-align:center;"> 290 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 </td>
   <td style="text-align:center;"> 0.878 </td>
   <td style="text-align:center;"> 0.928 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 Adj. </td>
   <td style="text-align:center;"> 0.878 </td>
   <td style="text-align:center;"> 0.927 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> AIC </td>
   <td style="text-align:center;"> 2208.5 </td>
   <td style="text-align:center;"> 1379.3 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> BIC </td>
   <td style="text-align:center;"> 2228.8 </td>
   <td style="text-align:center;"> 1397.6 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Log.Lik. </td>
   <td style="text-align:center;"> −1099.240 </td>
   <td style="text-align:center;"> −684.649 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> F </td>
   <td style="text-align:center;"> 1035.486 </td>
   <td style="text-align:center;"> 1221.381 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> RMSE </td>
   <td style="text-align:center;"> 3.05 </td>
   <td style="text-align:center;"> 2.56 </td>
  </tr>
</tbody>
<tfoot><tr><td style="padding: 0; " colspan="100%">
<sup></sup> + p &lt; 0.1, * p &lt; 0.05, ** p &lt; 0.01, *** p &lt; 0.001</td></tr></tfoot>
</table>

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-14-1.png" width="672" /><img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-14-2.png" width="672" />

While both of these models have relatively high in-sample fit, they both interestingly have a much smaller range of out-of-sample errors than our previous models. The post-84 model appears especially strong in this metric, with a histogram of out-of-sample errors centered around zero. Though the spread of the out-of-sample errors appears quite large, this is likely because the error measures are relatively small, therefore not detracting from this model's strength. I again explored how this would translate to predictions.

Post 1984 Model:


Table: <span id="tab:unnamed-chunk-15"></span>Table 1: Prediction (Post 1984 Data)

|     State      | Predicted Winner | Democratic Vote Share | Low Pred | High Pred |
|:--------------:|:----------------:|:---------------------:|:--------:|:---------:|
|    Arizona     |       DEM        |         51.84         |  49.95   |   50.71   |
|    Georgia     |       DEM        |         50.53         |  50.33   |   51.08   |
|    Michigan    |       DEM        |         52.43         |  51.40   |   52.15   |
|     Nevada     |       DEM        |         51.67         |  51.09   |   51.79   |
| North Carolina |       DEM        |         51.00         |  50.24   |   50.95   |
|  Pennsylvania  |       DEM        |         52.64         |  51.16   |   51.87   |
|   Wisconsin    |       DEM        |         51.98         |  51.31   |   52.08   |

Next, given the argument made by Shaw and Petrocik (5), as also addressed by Matt Dardet, that turnout does not predict party-specific outcomes, I was interested in seeing how my models would perform without the lagged turnout variable.

## Update 4: Removing Lagged Turnout

<table style="NAborder-bottom: 0; width: auto !important; margin-left: auto; margin-right: auto;" class="table">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:center;"> &amp;nbsp;Post 84 </th>
   <th style="text-align:center;"> &amp;nbsp;Post 96 </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:center;"> −2.836* </td>
   <td style="text-align:center;"> −2.561* </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (1.350) </td>
   <td style="text-align:center;"> (1.221) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> GDP_growth_quarterly </td>
   <td style="text-align:center;"> −0.236*** </td>
   <td style="text-align:center;"> −0.330*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.036) </td>
   <td style="text-align:center;"> (0.033) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> mean_5_wk_poll_support </td>
   <td style="text-align:center;"> 0.726*** </td>
   <td style="text-align:center;"> 0.830*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.030) </td>
   <td style="text-align:center;"> (0.036) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> unemployment </td>
   <td style="text-align:center;"> −0.396** </td>
   <td style="text-align:center;"> −0.538*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.121) </td>
   <td style="text-align:center;"> (0.122) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> log(total_grant) </td>
   <td style="text-align:center;"> 0.869*** </td>
   <td style="text-align:center;"> 0.419* </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.180) </td>
   <td style="text-align:center;"> (0.192) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> D_pv_lag1 </td>
   <td style="text-align:center;"> 0.273*** </td>
   <td style="text-align:center;"> 0.276*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.031) </td>
   <td style="text-align:center;"> (0.035) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> D_pv_lag2 </td>
   <td style="text-align:center;"> 0.032 </td>
   <td style="text-align:center;"> 0.016 </td>
  </tr>
  <tr>
   <td style="text-align:left;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.029) </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.030) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Num.Obs. </td>
   <td style="text-align:center;"> 434 </td>
   <td style="text-align:center;"> 290 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 </td>
   <td style="text-align:center;"> 0.894 </td>
   <td style="text-align:center;"> 0.948 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> R2 Adj. </td>
   <td style="text-align:center;"> 0.893 </td>
   <td style="text-align:center;"> 0.946 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> AIC </td>
   <td style="text-align:center;"> 2153.3 </td>
   <td style="text-align:center;"> 1291.6 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> BIC </td>
   <td style="text-align:center;"> 2185.9 </td>
   <td style="text-align:center;"> 1321.0 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Log.Lik. </td>
   <td style="text-align:center;"> −1068.664 </td>
   <td style="text-align:center;"> −637.809 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> F </td>
   <td style="text-align:center;"> 602.696 </td>
   <td style="text-align:center;"> 852.690 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> RMSE </td>
   <td style="text-align:center;"> 2.84 </td>
   <td style="text-align:center;"> 2.18 </td>
  </tr>
</tbody>
<tfoot><tr><td style="padding: 0; " colspan="100%">
<sup></sup> + p &lt; 0.1, * p &lt; 0.05, ** p &lt; 0.01, *** p &lt; 0.001</td></tr></tfoot>
</table>

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-16-1.png" width="672" /><img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-16-2.png" width="672" />

Somewhat aligning with Shaw and Petrocik's argument, the out-of-sample error range appears to be slightly smaller than when turnout was included. However, these errors are still significantly larger than when only the three strongly predictive variables were included. Again, I include election predictions for reference.

Post 1984 Model:


Table: <span id="tab:unnamed-chunk-17"></span>Table 2: Prediction (Post 1984 Data)

|     State      | Predicted Winner | Democratic Vote Share | Low Pred | High Pred |
|:--------------:|:----------------:|:---------------------:|:--------:|:---------:|
|    Arizona     |       DEM        |         50.33         |  50.54   |   52.06   |
|    Georgia     |       DEM        |         50.70         |  50.27   |   51.53   |
|    Michigan    |       DEM        |         51.78         |  51.77   |   52.94   |
|     Nevada     |       DEM        |         51.44         |  51.25   |   52.40   |
| North Carolina |       DEM        |         50.60         |  50.47   |   51.67   |
|  Pennsylvania  |       DEM        |         51.51         |  51.68   |   52.97   |
|   Wisconsin    |       DEM        |         51.69         |  51.54   |   52.80   |

Post 1996 Model:


Table: <span id="tab:unnamed-chunk-18"></span>Table 3: Prediction (Post 1984 Data)

|     State      | Predicted Winner | Democratic Vote Share | Low Pred | High Pred |
|:--------------:|:----------------:|:---------------------:|:--------:|:---------:|
|    Arizona     |       DEM        |         51.30         |  50.54   |   52.06   |
|    Georgia     |       DEM        |         50.90         |  50.27   |   51.53   |
|    Michigan    |       DEM        |         52.36         |  51.77   |   52.94   |
|     Nevada     |       DEM        |         51.82         |  51.25   |   52.40   |
| North Carolina |       DEM        |         51.07         |  50.47   |   51.67   |
|  Pennsylvania  |       DEM        |         52.32         |  51.68   |   52.97   |
|   Wisconsin    |       DEM        |         52.17         |  51.54   |   52.80   |

These results show a more certain Democratic victory than if turnout was not included.

Moving forward, there are a few additional steps I would like to take. First, I would like to incorporate the Supreme Court precedent data that I modified to include whether or not the shifts were accompanied by a conservative shift in the "median justice" of the court, as described by Rubin in Axios (5). In particular, I would like to evaluate the effect of an interaction term between precedent changes and the court's ideological shifts. However, following this, I am interested in running these models, especially the models that include more than the three highly predictive variables, through Elastic Net in order to engage in feature selection.

# References

1.  Julia. 2020. “Answer to ‘Export R Data to Csv.’” *Stack Overflow*. <https://stackoverflow.com/a/62017887>.; Bobbitt, Zach. 2023. “How to Convert Datetime to Date in R.” Statology. January 25, 2023. <https://www.statology.org/r-convert-datetime-to-date/>. GKi. 2023. “Answer to ‘Extract Month and Year From Date in R.’” *Stack Overflow*. <https://stackoverflow.com/a/76709941>. rafa.pereira. 2016. “Answer to ‘Extract Month and Year From Date in R.’” *Stack Overflow*. <https://stackoverflow.com/a/37704385>.; “Extract the Last N Characters from String in R - Spark By {Examples}.” n.d. Accessed October 26, 2024. <https://sparkbyexamples.com/r-programming/extract-the-last-n-characters-from-string-in-r/>.; Rubin, April. 2023. “Supreme Court Ideology Continues to Lean Conservative, New Data Shows.” Axios. July 3, 2023. https://www.axios.com/2023/07/03/supreme-court-justices-political-ideology-chart.
2.  Andina, Matias. 2016. “Answer to ‘How to Remove \$ and % from Columns in R?’” *Stack Overflow*. <https://stackoverflow.com/a/35757945>.; camille. 2022. “Answer to ‘Convert Column Names to Title Case.’” *Stack Overflow*. <https://stackoverflow.com/a/70804865>.
3.  Andina, Matias. 2016. “Answer to ‘How to Remove \$ and % from Columns in R?’” *Stack Overflow*. <https://stackoverflow.com/a/35757945>. “RPubs - Linear Regression Confidence and Prediction Intervals.” n.d. Accessed October 26, 2024. <https://rpubs.com/aaronsc32/regression-confidence-prediction-intervals>.
4.  “How to Replace Values in R with Examples - Spark By {Examples}.” n.d. Accessed October 26, 2024. <https://sparkbyexamples.com/r-programming/replace-values-in-r/>. camille. 2022. “Answer to ‘Convert Column Names to Title Case.’” *Stack Overflow*. <https://stackoverflow.com/a/70804865>.
5. Rubin, April. 2023. “Supreme Court Ideology Continues to Lean Conservative, New Data Shows.” Axios. July 3, 2023. https://www.axios.com/2023/07/03/supreme-court-justices-political-ideology-chart.

# Data Sources

All data sources are provided by GOV 1372 course staff

Popular Vote Datasets

-   National Popular Vote Data from Wikipedia, Abramowitz (2020), Abramowitz (2020) replication data, and manual changes

-   State Popular Vote Data from MIT elections project, Wikipedia, and manual editing

Economic Data

-   FRED Data from St. Louis FRED

-   Grants Data from Kriner and Reeves (2015) replication data

Polling Data

-   State Polls from FiveThirtyEight poll averages and preprocessing

Data sources for state and county-level turnout and Supreme Court cases are unknown, but were generously provided by the GOV 1372 course staff. However, I append the Supreme Court data with a metric of how the Supreme Court's leaninted over time with data from Axios (Rubin, April. 2023. “Supreme Court Ideology Continues to Lean Conservative, New Data Shows.” Axios. July 3, 2023. https://www.axios.com/2023/07/03/supreme-court-justices-political-ideology-chart.
)

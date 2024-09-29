---
title: 'Week 4: Incumbency'
author: Package Build
date: '2024-09-25'
slug: week-4-incumbency
categories: []
tags: []
---
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />

In this week's lab, we explore the impact of candidate or party incumbency on presidential election outcomes. More specifically, we ask "How should we treat the incumbency advantage in our 2024 electoral foreasts?". As always, my thanks to Matthew Dardet for his helpful starter code.




This week, we reviewed a canonically successful model used to predict the advantage of incumbency: the Time for Change Model by Alan Abramowitz. This relatively simple model -- an OLS regression with independent variables of Quarter 2 GDP, June Gallup poll approval, and whether or not one is an incumbent -- is modeled and tested here.


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


# Citations:
 
 (1) Hlavac, Marek (2022). stargazer: Well-Formatted Regression and Summary Statistics Tables.
 R package version 5.2.3. https://CRAN.R-project.org/package=stargazer 
 (2): Model Summary Package

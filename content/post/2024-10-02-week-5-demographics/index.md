---
title: Week 5 - Demographics
author: Shriya Yarlagadda
date: '2024-10-02'
slug: week-5-demographics
categories: []
tags: []
---
<script src="{{< blogdown/postref >}}index_files/kePrint/kePrint.js"></script>
<link href="{{< blogdown/postref >}}index_files/lightable/lightable.css" rel="stylesheet" />






This week, we explore the impact of demographics on voter turnout, asking "What are the connections, if any, between demographics and voter turnout? Can demographics and turnout be used to predict election outcomes? If so, how and how well?" Thank you, as always, to Matthew Dardet for his starter code and coding assistance. I also thank Jacqui Schlesinger, my partner for this week's in-class presentation, for her valuable thoughts and advice on interesting visualizations.

To answer this question, we worked to replicate the work of Kim and Zilinsky (2023) to a degree (3). Their work sought to determine if certain demographic factors were actually predictive of voter behavior. While they also considered "tree-based machine learning models" (pg. 67), some code for which is included in a comment in my code for this blog, I focused on building a logistic regression model here. In particular, I trained models to predict both presidential vote and the act of turning out to vote itself, based on available demographic data from the 2016 American National Election Survey (ANES). 

I separated this data into two datasets (one for each model). The first dataset, used for my presidential vote choice model, dropped all datapoints where a survey respondent's vote was not available (indicating that they did not vote). The second, used for my turnout model, incorporated all datapoints from the original ANES data that we used, but included a separate variable indicating turnout, where all responses not including their choice of candidate were marked as not having turned out to vote and those with any response marked as having turned out.

Importantly, building this model required creating numerous factor variables. Given that certain demographic variables like gender naturally exist in categories, rather than as a numeric quantity that can increase in value in conjunction with an outcome like vote choice, I created separate dummies to represent each category of several model inputs, namely gender, race, religion, marriage status, homeownership status, and work status. 



<table style="NAborder-bottom: 0; width: auto !important; margin-left: auto; margin-right: auto;" class="table">
 <thead>
  <tr>
   <th style="text-align:left;">   </th>
   <th style="text-align:center;"> Turnout </th>
   <th style="text-align:center;"> &amp;nbsp;Presidential Vote </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> (Intercept) </td>
   <td style="text-align:center;"> 13.518 </td>
   <td style="text-align:center;"> 3.872*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (196.969) </td>
   <td style="text-align:center;"> (0.976) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> genderMale </td>
   <td style="text-align:center;"> 0.225 </td>
   <td style="text-align:center;"> 1.301 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.569) </td>
   <td style="text-align:center;"> (0.879) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> genderFemale </td>
   <td style="text-align:center;"> 0.165 </td>
   <td style="text-align:center;"> 0.895 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.568) </td>
   <td style="text-align:center;"> (0.878) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> genderOther </td>
   <td style="text-align:center;"> −0.139 </td>
   <td style="text-align:center;"> −13.229 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.935) </td>
   <td style="text-align:center;"> (459.700) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raceBlack </td>
   <td style="text-align:center;"> −0.339* </td>
   <td style="text-align:center;"> −4.262*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.144) </td>
   <td style="text-align:center;"> (0.391) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raceHispanic </td>
   <td style="text-align:center;"> 0.110 </td>
   <td style="text-align:center;"> −1.979*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.134) </td>
   <td style="text-align:center;"> (0.233) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raceOther/Multiple </td>
   <td style="text-align:center;"> 0.646*** </td>
   <td style="text-align:center;"> −0.954*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.140) </td>
   <td style="text-align:center;"> (0.232) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> raceMissing </td>
   <td style="text-align:center;"> −0.017 </td>
   <td style="text-align:center;"> −0.714 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.688) </td>
   <td style="text-align:center;"> (0.982) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> educ </td>
   <td style="text-align:center;"> −0.379*** </td>
   <td style="text-align:center;"> −0.411*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.050) </td>
   <td style="text-align:center;"> (0.073) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> income </td>
   <td style="text-align:center;"> −0.177*** </td>
   <td style="text-align:center;"> −0.100+ </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.040) </td>
   <td style="text-align:center;"> (0.058) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> religionProtestant </td>
   <td style="text-align:center;"> −12.324 </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (196.968) </td>
   <td style="text-align:center;">  </td>
  </tr>
  <tr>
   <td style="text-align:left;"> religionCatholic </td>
   <td style="text-align:center;"> −12.331 </td>
   <td style="text-align:center;"> −0.354* </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (196.968) </td>
   <td style="text-align:center;"> (0.139) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> religionJewish </td>
   <td style="text-align:center;"> −12.885 </td>
   <td style="text-align:center;"> −1.441*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (196.968) </td>
   <td style="text-align:center;"> (0.376) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> religionOther </td>
   <td style="text-align:center;"> −12.103 </td>
   <td style="text-align:center;"> −0.728*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (196.968) </td>
   <td style="text-align:center;"> (0.144) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> attend_church </td>
   <td style="text-align:center;"> 0.047+ </td>
   <td style="text-align:center;"> −0.317*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.028) </td>
   <td style="text-align:center;"> (0.039) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> southern </td>
   <td style="text-align:center;"> −0.061 </td>
   <td style="text-align:center;"> −0.707*** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.087) </td>
   <td style="text-align:center;"> (0.126) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> work_statusUnemployed </td>
   <td style="text-align:center;"> 0.287* </td>
   <td style="text-align:center;"> −0.007 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.136) </td>
   <td style="text-align:center;"> (0.233) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> work_statusRetired </td>
   <td style="text-align:center;"> 0.040 </td>
   <td style="text-align:center;"> −0.259 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.147) </td>
   <td style="text-align:center;"> (0.180) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> work_statusHomemaker </td>
   <td style="text-align:center;"> −0.074 </td>
   <td style="text-align:center;"> 0.882** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.184) </td>
   <td style="text-align:center;"> (0.275) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> work_statusStudent </td>
   <td style="text-align:center;"> −0.325 </td>
   <td style="text-align:center;"> −0.253 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.270) </td>
   <td style="text-align:center;"> (0.454) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> work_statusMissing </td>
   <td style="text-align:center;"> −0.227 </td>
   <td style="text-align:center;"> −13.455 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (1.303) </td>
   <td style="text-align:center;"> (882.744) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> homeownerNo </td>
   <td style="text-align:center;"> 0.188+ </td>
   <td style="text-align:center;"> −0.342* </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.097) </td>
   <td style="text-align:center;"> (0.140) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> homeownerMissing </td>
   <td style="text-align:center;"> 0.851 </td>
   <td style="text-align:center;"> 1.381 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.601) </td>
   <td style="text-align:center;"> (1.253) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> marriedNever married </td>
   <td style="text-align:center;"> −0.098 </td>
   <td style="text-align:center;"> −0.525** </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.127) </td>
   <td style="text-align:center;"> (0.190) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> marriedDivorced </td>
   <td style="text-align:center;"> −0.087 </td>
   <td style="text-align:center;"> 0.199 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.131) </td>
   <td style="text-align:center;"> (0.173) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> marriedSeparated </td>
   <td style="text-align:center;"> 0.518+ </td>
   <td style="text-align:center;"> 0.307 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.273) </td>
   <td style="text-align:center;"> (0.482) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> marriedWidowed </td>
   <td style="text-align:center;"> 0.013 </td>
   <td style="text-align:center;"> −0.250 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.178) </td>
   <td style="text-align:center;"> (0.235) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> marriedPartners </td>
   <td style="text-align:center;"> 0.030 </td>
   <td style="text-align:center;"> −0.269 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.142) </td>
   <td style="text-align:center;"> (0.225) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> marriedMissing </td>
   <td style="text-align:center;"> −0.555 </td>
   <td style="text-align:center;"> 1.596 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (1.318) </td>
   <td style="text-align:center;"> (1.667) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> age_subset30-44 </td>
   <td style="text-align:center;"> −0.085 </td>
   <td style="text-align:center;"> −0.279 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.134) </td>
   <td style="text-align:center;"> (0.232) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> age_subset45-59 </td>
   <td style="text-align:center;"> −0.529*** </td>
   <td style="text-align:center;"> −0.029 </td>
  </tr>
  <tr>
   <td style="text-align:left;">  </td>
   <td style="text-align:center;"> (0.142) </td>
   <td style="text-align:center;"> (0.230) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> age_subset60+ </td>
   <td style="text-align:center;"> −0.990*** </td>
   <td style="text-align:center;"> −0.115 </td>
  </tr>
  <tr>
   <td style="text-align:left;box-shadow: 0px 1.5px">  </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.173) </td>
   <td style="text-align:center;box-shadow: 0px 1.5px"> (0.256) </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Num.Obs. </td>
   <td style="text-align:center;"> 3116 </td>
   <td style="text-align:center;"> 1924 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> AIC </td>
   <td style="text-align:center;"> 3868.7 </td>
   <td style="text-align:center;"> 2098.4 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> BIC </td>
   <td style="text-align:center;"> 4062.1 </td>
   <td style="text-align:center;"> 2270.8 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Log.Lik. </td>
   <td style="text-align:center;"> −1902.355 </td>
   <td style="text-align:center;"> −1018.196 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> RMSE </td>
   <td style="text-align:center;"> 0.46 </td>
   <td style="text-align:center;"> 0.42 </td>
  </tr>
</tbody>
<tfoot><tr><td style="padding: 0; " colspan="100%">
<sup></sup> + p &lt; 0.1, * p &lt; 0.05, ** p &lt; 0.01, *** p &lt; 0.001</td></tr></tfoot>
</table>




``` r
# Print table after a few lines to have gap
knitr::kable(rbind(turnout_val, pres_vote_val), col.names = c("Value", "In-Sample Accuracy", "Out-of-Sample Accuracy"))
```



|Value             | In-Sample Accuracy| Out-of-Sample Accuracy|
|:-----------------|------------------:|----------------------:|
|Turnout           |             0.6711|                 0.6615|
|Presidential Vote |             0.7370|                 0.7354|


It appears that a logistic regression of these selected variables only predicts both a voter's decision to turn out and the likelihood of their vote for a particular party about 65-75% of the time. Although these models are slightly different from Kim and Zilinsky's and are slightly more accurate, they nonetheless provide relatively low certainty of an accurate prediction. However, these regressions appeared to have some statistically significant coefficients. Interestingly, education level and identification as someone of multiple races (or one that was not otherwise identified by the ANES) or Black were the only variables that were statistically significant predictors of both turnout and vote choice (assuming an alpha level of 0.05). Turnout was also largely predicted by income, unemployment status, and age above 45, while vote choice was predicted by identification as Hispanic, Catholicism, Judaism, other religion, church attendance frequency, location in the US South, status as a homemaker, homeownership, and marriage status. Most interesting to me, though, is that gender does not appear to significantly predict either outcome.

Given these results, I wanted to visualize how several of these characteristics have played out in key battleground states, using voter roll data generously provided by Statara. This information could theoretically provide important information regarding how my findings from survey data could translate into the real world. I produced graphs for Arizona, Michigan, Georgia, and Nevada, while my partner for this week's in-class presentation, Jacqui, focused on making graphs for Wisconsin, Pennsylvania, and North Carolina.

While I could not visualize how these demographics related to vote choice, as this information is not captured in voter rolls, I visualized variations in the proportion of people in each group who turned out to vote in the 2020 presidential election. This is not a perfect measure of turnout, especially for the 2024 election. Aside from the 2020 election being impacted by the COVID-19 pandemic, my use of voter roll data precludes me from accessing the most accurate measure of national turnout, because those who take the time to register on the voter roll (a necessary step to even vote) are logically more likely to turn out to vote at any given election than those who do not (6). However, keeping in mind that this data only represents those who have registered to vote, these results show some interesting conclusions.


<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-6-1.png" width="672" /><img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-6-2.png" width="672" /><img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-6-3.png" width="672" /><img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-6-4.png" width="672" /><img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-6-5.png" width="672" />

These results show that females and older people consistently turn out at higher rates than males and younger people in each of the selected states. This is interesting when considering that our logistic regression found this difference to not be statistically significant in a national sample. Similarly, voters of a racial category other than the ones identified in voter files appear to have higher turnout rates than any other category in all of these states. Interestingly, Hispanic voters have the lowest turnout rates in each of these states except Nevada, voters with a vocational education tend to turn out more than those with only some college education, and there does not appear to be a strong difference between turnout for rural and suburban voters in each of these states. 





# References:

“Answer to ‘How Do I Undo the Most Recent Local Commits in Git?’” 2009. Stack Overflow. https://stackoverflow.com/a/927386.

(1) Ahorn. 2020. “Answer to ‘Export R Data to Csv.’” Stack Overflow. https://stackoverflow.com/a/62006344.

(2)  dickoa. 2012. “Answer to ‘Read All Files in a Folder and Apply a Function to Each Data Frame.’” Stack Overflow. https://stackoverflow.com/a/9565134; Guidance from Matt Dardet in office hours

(3) Kim, Seo-young Silvia, and Jan Zilinsky. 2024. “Division Does Not Imply Predictability: Demographics Continue to Reveal Little About Voting and Partisanship.” Political Behavior 46 (1): 67–87. https://doi.org/10.1007/s11109-022-09816-z.

(4) GLM help page

(5) Tibble Row help page - as used in previous blogs

(6) Hartig, Hannah, Andrew Daniller, Scott Keeter, and Ted Van Green. 2023. “1. Voter Turnout, 2018-2022.” Pew Research Center (blog). July 12, 2023. https://www.pewresearch.org/politics/2023/07/12/voter-turnout-2018-2022/.


(7) aosmith. 2014. “Answer to ‘Why Are My Dplyr Group_by & Summarize Not Working Properly? (Name-Collision with Plyr).’” Stack Overflow. https://stackoverflow.com/a/26933112.; GGPlot help page; 
stevec. 2020. “Answer to ‘Adding Data Labels above Geom_col() Chart with Ggplot2.’” Stack Overflow. https://stackoverflow.com/a/61574728.; GeomText Help Page; Geom_Col help page; duhaime. 2018. “Answer to ‘Remove Legend Ggplot 2.2.’” Stack Overflow. https://stackoverflow.com/a/51923574.


(8) Scale Manual Help Page; Geom Label Help Page; stefan. 2021. “Answer to ‘How to Center Labels over Side-by-Side Bar Chart in Ggplot2.’” Stack Overflow. https://stackoverflow.com/a/70197229.; duhaime. 2018. “Answer to ‘Remove Legend Ggplot 2.2.’” Stack Overflow. https://stackoverflow.com/a/51923574.



# Data Sources

American National Election Survey (ANES)

Subsetted version of state voter files (Statara)

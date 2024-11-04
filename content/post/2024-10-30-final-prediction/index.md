---
title: "Final Prediction"
author: "Shriya Yarlagadda"
date: "2024-10-30"
slug: "final-prediction"
categories: []
tags: []
editor_options: 
  markdown: 
    wrap: sentence
---



For my final weekly blog post, I produced my final prediction model for the 2024 US Presidential Election.









## Methodological Note

Each of the models that I have developed over the past few weeks have predicted a strong performance for Vice President Harris in all seven predicted "swing" states (4) . While this does not necessarily align with what some major forecasters predict for the election (4), it is unclear how to evaluate the performance of these models without relying on this benchmark.

In my previous blogs, I used out-of-sample cross validation to evaluate my models, leaving out a random set of years during each repetition of training my model and testing how well the subsetted model performed on the left-out years. In doing so, I was able to test how well my model predicted state-level outcomes for the average election between either 1984 and 2020 or 1996 and 2020 (depending on the dataset that was used). 

However, as we have discussed in class, there might be several factors that differentiate this election from others. If this is the case, the underlying factors that shape voter behavior -- and would thus be included in an election prediction model -- may change from election to election. Given that our task is to build a model that best predicts the upcoming 2024 US Presidential Election, aiming to predict voter behavior in the "average" election may not best predict a specific one.

In this blog, I have decided to evaluate my models based on *how well they predict the outcome of the 2016 election* (when the 2016 election is excluded from the data).This is because I argue that the 2016 election is the closest available analog to the upcoming election, with Donald Trump once again running against a female Democrat, replacing a male incumbent Democrat in a growing economy (as indicated by a 2016 Q3 GDP growth rate of 2.9 and a 2024 Q3 GDP growth rate of 2.8) (5). By testing how well each model does in predicting a similarly structured election, we can effectively control for a number of candidate and contextual characteristics -- which could conceivably affect how voters choose to cast their ballots (6).

While one might instead consider 2020, given its comparative recency, the fact that the year constituted an economic (as we discussed in Week 2) and situational outlier (with the COVID-19 pandemic) makes it difficult for us to compare the elections (7).










## Model Testing

Going into this week, I was interested in testing eight OLS models predicting Democratic vote share that I built last week (four models across two sets of data), using leave-one-out out of sample validation. Thank you, again, to Matt Dardet for his starter code.

However, I wanted to consider two additional pieces of data. First, I consider data from the Cost of Voting Index, a metric created by Pomante that reflects the degree of challenge that voters face when seeking to cast their ballot (10). Second, I added data regarding the Supreme Court's overturning of precedent, specifically adding an interaction term between the number of precedents the court overturned in the previous four years and an indicator variable that representing whether the court had a conservative shift in its decisionmaking that I created using data from Rubin, 2023 (11). As discussed in our course, election laws -- and the guidelines that they may place on who is able to cast a vote -- could have a substantial impact on elections, especially through disproportionately affecting certain demographic groups (12). Similarly, rhetoric regarding the Supreme Court's overturning of Roe v. Wade and the potential for the next president to shape the Supreme Court's makeup has also impacted campaign strategies, leading me to consider how this may be predictive in this upcoming election (13) 

Importantly, I also updated my training data since last week, replacing the variable of mean poll predictions five weeks out from the election with poll predictions one week out from the election. Aside from the fact that this data is now available, this metric also allows me to better account for the underlying factor that I hope to include in my model -- polling predictions. Additionally, recognizing that my metric of grant allocation was incorrectly measured, I slightly altered it. In previous weeks, I calculated one metric of grant spending across decades for each state, rather than calculating spending in the year or years prior to an election. This variable in this form definitely did not drive voting outcomes, as it would be impossible for someone in, for example, the 2000 election to predict how funds would be allocated to their state from 2000 to 2008. Instead, I summed the total funding allocated to each state during the previous election cycle, but still took the log of this metric given the shape of the data. While this metric is slightly different than the one that Kriner and Reeves used in their study finding significant results (they focused on testing recency bias in voting by focusing on funding allocated in the year before an election), this metric also allows us to aggregate upwards, potentially limiting the missing data challenges from not having data for elections after 2008 (14)

Including these new variables, I tested a total of 32 different OLS regression models predicting Democratic vote share using leave-one-out out-of-sample validation, creating four versions of each of the eight models from last week - one original, one including the Cost of Voting Index, one including the Supreme Court shift interaction term, and one including both. 

To evaluate the success of each model, I calculated the prediction error (between the OLS predicted value and the true Democratic vote share) for the 2016 election in each state. Then, I subsetted to states that have been considered "battlegrounds" in the upcoming election, calculating the mean error of only these seven states (4). I decided to subset to only battlegrounds because, barring the surprise flipping of a state, many commentators argue that these states are the ones that will drive the election's outcome (4). Therefore, I want to select a model that does the best job at predicting the outcomes of these states. 

One primary limitation of this approach is that certain characteristics of these states, such as their demographics or issues of interest, may have changed slightly between 2016 and 2024 - a future iteration of this project may want to consider adding additional weights to consider these differences. However, under the assumption that each swing state in 2024 is more like itself in 2016 than the average state, this the subsetted model should theoretically offer better predictions.

I ultimately selected the model with the lowest mean prediction error out of these subsetted data (1.65 percentage points), running the model through ElasticNet to produce my ultimate prediction model (using starter code from Matt Dardet). This model is the one described below. When using ElasticNet, I found a lambda value of 0.03 for this Democratic model. In order to also find a comparable value for Republican vote share to predict two-party vote share, I also trained a second model with the same parameters of my primary model to predict Republican vote share. Again, I found the same lambda value of 0.03 when running this model through ElasticNet. However, I emphasize that my Democratic prediction model is the one that I put forward as "my" model in this project.








# My Final Prediction

### Final Model and Description

My final model is a regularized OLS linear regression model aimed at predicting Democratic vote share, including five parameters.

At the national level, I only include one variable - the interaction between the conservatism of the Supreme Court and the number of precedents that it overturned in the prior four years.

At the state level, thus varying across both elections and state, I include average poll support one week out from the election, Democratic vote share in the previous two elections, and the Cost of Voting Index. The coefficients of this model -- both in its original OLS form and when regularized using Elastic Net -- are listed below, based upon starter code from Matt Dardet.

Notably, I also dropped training data from Washington DC, following the precedent that we adopted in Week 1 of our course given its status as a strongly Democratic outlier.

### Coefficients and Interpretation



|      Coefficient       |    OLS     | Elastic Net |
|:----------------------:|:----------:|:-----------:|
| mean_1_wk_poll_support | 0.7836543  |  0.7737130  |
|       D_pv_lag1        | 0.4170495  |  0.4082948  |
|       D_pv_lag2        | -0.0986788 | -0.0810606  |
|      InitialCOVI       | 0.0443900  |  0.0195551  |
|      sc_interact       | 0.1792211  |  0.1799611  |

Interpreting the Elastic Net coefficients, I find the following interpretations of my model:

1) Mean_1_wk_poll_support: Holding all other variables constant, a one percent point increase in poll support for a Democratic candidate one week out from the election results in only a 0.774 percentage point increase in their predicted vote share

2) D_pv_lag1: Holding all other variables constant, a one percentage point increase in the vote share that the Democratic candidate received in the last election corresponds to a 0.41 percentage point increase in a candidate's predicted vote share

3) D_pv_lag2: Holding all other variables constant, a one percentage point increase in the vote share that the Democratic candidate received in the second-to-last election corresponds to a 0.08 percentage point decrease in a candidate's predicted vote share

4) InitialCOVI: Holding all other variables constant, a one unit increase in the Cost of Voting Index score results in a 0.02 percentage point increase in a candidate's predicted vote share

5) Sc_interact: Holding all other variables constant and assuming a conservative shift, each additional precedent overturn during the four years prior to an election increases a candidate's predicted vote share by 0.18 percentage points.

These coefficients, especially D_pv_lag2, seem quite counterintuitive to me. However, it is interesting to me that the ultimate results of my model seem relatively close to what major pollsters are predicting. (8)

### Validation

The final OLS model has high internal validity, with an adjusted R^2 value of 0.9455. As demonstrated earlier, the model also has higher leave-one-out out-of-sample performance than any of the other models that I tested, predicting 2016 results. However, I also include a histogram of errors when conducting a more generalized cross-validation test. Thank you, again to Matt for his starter code.

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-14-1.png" width="672" />

Aside from the occasional large negative outlier, this model also generally performs well across elections, with mean errors centered around 0. It is especially interesting that the average error skews slighly negative, meaning that, if anything, the model tends to underpredict Democratic performance on average.

## Justification

### What I considered

While my ultimate selection of this model is based upon strong performance under leave-one-out cross validation, I also want to highlight why I selected the variables that I included in my initial few models.

I was initially inspired by one of the most "parsimonious" (as referred to by Matt Dardet) election prediction models that we have studied in GOV 1372 - Alan Abramowitz's Time for Change Model from Week 4. However, I wanted to develop a model that would have predictive power for non-incumbents, especially given that it is hard to afford the incumbency advantage to either of the candidates in this election (as we discussed in Week 4).

Because of this, I started with one of the "fundamental" features that was included in the Time for Change model -- GDP growth in the quarter before the election. I also complemented this with measures of unemployment - a metric that perhaps has a greater effect one's day-to-day lifestyle than could be measured by GDP growth. In doing so, I wanted to adopt the "fundamentals" strategy that many election forecasters, including Tien & Lewis-Beck and Morris, incorporate into their models, considering the centrality of economic variables in a voter's decisionmaking calculus (16). In particular, it felt vital to consider these factors at a national level, especially given our discussion about how national level metrics of economic performance tend to better predict outcomes than those measured at a more local level (17)

Adding to this, I also wanted to consider the influence of polls - a metric notably included in several prominent popular forecasts, including those by Morris and Silver, as well as academic models like Pollyvote (18).

Then, I considered several additional factors based on our findings from previous blogs and our discussion of potentially relevant factors in this election. Aside from the COVI and Supreme Court Interaction metrics as justified earlier, I considered metrics of grant spending and turnout. I included grant spending because of Kriner and Reeves' finding that the variable was a significant predictor of outcomes (14). Finally, I considered previous Democratic vote share, given that it could provide an effective benchmark of previous state performance. In last week's blog, we see that these variables are highly predictive in a scatterplot.

I also considered including turnout in the previous election as a parameter to test. However, upon Matt Dardet's recommendation, I ultimately removed this parameter, reflecting Shaw and Petrocik's findings that turnout does not affect the polling results of either party (19). Nevertheless, I include models with and without this parameter for comparison in my code.

Using these metrics, I made the specific choice to predict Democratic vote share, rather than Democratic two-party vote share. Inspired by my classmate Alex Heuss, I believed that this metric would more appropriately reflect actual outcomes. Although there has not been a significant third-party candidate officially in the election since Robert Kennedy dropped out, the fact that his name remains on the ballot and many voters may vote for other candidates because of apathy towards both primary candidates may mean that this election cannot be truly considered a two-party race (20). 

### What I didn't include

Notably, I did not include any model components that directly measured either demographics or campaign events. As demonstrated by both Kim and Zilinsky's work, as well as my work which sought to replicate it, demographic factors arguably did not have a substantial predictive impact in our modeling (21). Similarly, my analysis of campaign events like advertising and campaign events did not prove to be significant, aligning (as I discussed in previous weeks), with Kalla and Broockman's work (22). However, it could be possible that, in the unique context of the 2024 election, these variables could be relevant. Therefore, I exclude these conditions with a degree of caution.

## Limitations

There are several notable limitations to immediately note with my model. 

First, I faced significant missing data challenges with my variable for lagged turnout, with many states missing this information. This may have affected the outcomes of the regressions that considered this variable. Similarly, my vote share data did not include outcomes at the district level for Maine and Nebraska. Although I manually added these data to my test data, the lack of these data points in my training data could have conceivably affected my model training. Finally, since we do not have polling data available for every state, I was not able to produce final predictions for every state. 

Second, the dataset on federal grant allocation that we had access to only calculates grant spending up to 2008, causing me to use 2008 data for all future elections. Again, this likely affected the outcomes of my regressions.

Third, unlike prominent pollsters like Morris, I averaged the values of all polls without considering their rating. This may have led to the overweighting of less reliable polls (18). 

Finally, it may be possible that the underlying data in each of these models may have a distribution that is not conducive to linear regression. This would make my choice of model -- selected initially for parsimony -- slightly ineffective. (23)

## Final Results

Below, I provide the final predictions from both the OLS and Regularized versions of my model for each of the battleground states (4). While I use the results of the regularized model as my final prediction, I include the OLS model as well because of our ability to generate more reliable confidence intervals for OLS models than regularized models (24). Given that the predictions for both are relatively similar, the OLS prediction intervals may provide a reasonable estimate of a range for the regularized model as well.

OLS Prediction (with intervals)


|     State      | Democratic Vote Share | Republican Vote Share | Predicted Winner | Low Dem Pred | High Dem Pred |
|:--------------:|:---------------------:|:---------------------:|:----------------:|:------------:|:-------------:|
|    Arizona     |         50.37         |         45.98         |       DEM        |    50.03     |     50.70     |
|    Georgia     |         50.61         |         46.24         |       DEM        |    50.18     |     51.04     |
|    Michigan    |         51.30         |         43.82         |       DEM        |    50.90     |     51.70     |
|     Nevada     |         50.66         |         42.89         |       DEM        |    49.87     |     51.45     |
| North Carolina |         50.19         |         46.24         |       DEM        |    49.84     |     50.53     |
|  Pennsylvania  |         51.05         |         45.04         |       DEM        |    50.74     |     51.37     |
|   Wisconsin    |         51.16         |         46.02         |       DEM        |    50.63     |     51.68     |

Regularized Prediction


|     State      | Predicted Winner | Democratic Vote Share | Republican Vote Share |
|:--------------:|:----------------:|:---------------------:|:---------------------:|
|    Arizona     |       DEM        |         50.29         |         46.00         |
|    Georgia     |       DEM        |         50.53         |         46.24         |
|    Michigan    |       DEM        |         51.27         |         43.89         |
|     Nevada     |       DEM        |         50.69         |         43.01         |
| North Carolina |       DEM        |         50.13         |         46.24         |
|  Pennsylvania  |       DEM        |         51.01         |         45.06         |
|   Wisconsin    |       DEM        |         51.07         |         46.00         |

Predicted Electoral Vote Count (for states with polling data)

| Harris | Trump |
|:------:|:-----:|
|  271   |  77   |

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-17-1.png" width="672" />

This model proves incredibly optimistic for the Harris campaign, resulting in wins in not only all of the battleground states, but also, curiously, Florida (although the margin in Florida is less than 0.15 percentage points and neither candidate earns over 50% of the vote). However, it is also interesting to consider that the prediction intervals of these measures may overlap with each other, such as in the case of Florida. While this does not necessarily align with what several pollsters predict for the election, it will be interesting to see how well this model shapes up in the final election! (4) Thank you again, as in all of the previous blogs, to Matt Dardet for his detailed starter code across the past several weeks, which I reference throughout this blog.

# References:

(1) Andina, Matias. 2016. “Answer to ‘How to Remove $ and % from Columns in R?’” Stack Overflow. https://stackoverflow.com/a/35757945.
Bobbitt, Zach. 2021. “How to Sort Values Alphabetically in R.” Statology. July 13, 2021. https://www.statology.org/sort-alphabetically-in-r/.
———. 2022. “How to Calculate Lagged Values in R (With Examples).” Statology. December 13, 2022. https://www.statology.org/r-lag/.
camille. 2022. “Answer to ‘Convert Column Names to Title Case.’” Stack Overflow. https://stackoverflow.com/a/70804865.
“Convert String to Upper Case, Lower Case, Title Case, or Sentence Case — Case.” n.d. Accessed October 21, 2024. https://stringr.tidyverse.org/reference/case.html.
Khalilov, Murad. 2024. “Answer to ‘Rename All Columns to Title Case with {dplyr}.’” Stack Overflow. https://stackoverflow.com/a/78146810.
“Reorder the Column of Dataframe in R Using Dplyr.” 2021. GeeksforGeeks. September 1, 2021. https://www.geeksforgeeks.org/reorder-the-column-of-dataframe-in-r-using-dplyr/.;  Rubin, April. 2023. “Supreme Court Ideology Continues to Lean Conservative, New Data Shows.” Axios. July 3, 2023. https://www.axios.com/2023/07/03/supreme-court-justices-political-ideology-chart

(2) Nelamali, Naveen. 2022. “Replace Values Based on Condition in R.” Spark By {Examples}. June 16, 2022. https://sparkbyexamples.com/r-programming/replace-values-based-on-condition-in-r/.; Shah, Ronak. 2021. “Answer to ‘How Can I Add a Row with the Mean of Each Numeric Column.’” Stack Overflow. https://stackoverflow.com/a/69264173.; “How to Replace Values in R with Examples - Spark By {Examples}.” n.d. Accessed November 1, 2024. https://sparkbyexamples.com/r-programming/replace-values-in-r/.

(3) Levinson, Andrew, Lakshmi Ketineni, and Dov Friedman. n.d.-a. “Maine Election 2016: Live Results.” WSJ. Accessed November 4, 2024. https://www.wsj.com/election/2016/general/state/maine.
———. n.d.-b. “Nebraska Election 2016: Live Results.” WSJ. Accessed November 4, 2024. https://www.wsj.com/election/2016/general/state/nebraska.
Nelamali, Naveen. 2022. “Replace Values Based on Condition in R.” Spark By {Examples}. June 16, 2022. https://sparkbyexamples.com/r-programming/replace-values-based-on-condition-in-r/; Shah, Ronak. 2021. “Answer to ‘How Can I Add a Row with the Mean of Each Numeric Column.’” Stack Overflow. https://stackoverflow.com/a/69264173.
———. 
“Live Election Results: 2020 Maine Results.” n.d. Accessed November 4, 2024. https://www.politico.com/2020-election/results/maine/.
“Nebraska Election Results 2020 | Live Map Updates | Voting by County & District.” n.d. Accessed November 4, 2024. https://www.politico.com/2020-election/results/nebraska/.; “How to Replace Values in R with Examples - Spark By {Examples}.” n.d. Accessed November 1, 2024. https://sparkbyexamples.com/r-programming/replace-values-in-r/.


(4) Eg: “2024 Presidential Election Predictions \| The Hill and DDHQ.” n.d. The Hill. Accessed October 31, 2024. <https://elections2024.thehill.com/forecast/2024/president/>. “Harris v Trump: 2024 Presidential Election Prediction Model.” n.d. The Economist. Accessed October 31, 2024. <https://www.economist.com/interactive/us-2024-election/prediction-model/president>. Morris, G. Elliott.
    2024. “Who Is Favored To Win The 2024 Presidential Election?” FiveThirtyEight. June 11, 2024. <https://projects.fivethirtyeight.com/2024-election-forecast/>.

(5)Eg: Fink, Jenni.
    2024. “How Donald Trump’s Chances Compare to Past Elections at 50 Day Mark - Newsweek.” Newsweek. September 17, 2024. <https://www.newsweek.com/donald-trump-presidential-polls-election-2024-1954820>. O’Connell, Ryan.
    2025. “Is This 2016 All Over Again?” The Globalist. October 2, 2024. <https://www.theglobalist.com/united-states-politics-2024-us-presidential-elections-kamala-harris-donald-trump/>. Paz, Christian.
    2026. “Can We Trust the Polls This Year?” Vox. September 10, 2024. <https://www.vox.com/2024-elections/370649/trust-polls-2016-2020-election-2024-pollster-polling-miss>. Rogerson, Riley.
    2027. “‘Déjà Vu All Over Again’: Senators Say the 2024 Race Is Suddenly Looking Like 2016.” NOTUS. August 2, 2024. <https://www.notus.org/congress/deja-vu-senators-2024-race-like-2016>.

(6) Eg: Coffé, Hilde, and Åsa von Schoultz.
    2021. “How Candidate Characteristics Matter: Candidate Profiles, Political Sophistication, and Vote Choice.” Politics 41 (2): 137–55. <https://doi.org/10.1177/0263395720922077>. ICPSR. n.d. “Candidate Characteristics.” ICPSR. Accessed October 31, 2024. <https://www.icpsr.umich.edu/web/pages/instructors/setups/notes/candidate-characteristics.html>. Kulachai, Waiphot, Unisa Lerdtomornsakul, and Patipol Homyamyen.
    2022. “Factors Influencing Voting Decision: A Comprehensive Literature Review.” Social Sciences 12 (9): 469. <https://doi.org/10.3390/socsci12090469>. Schwarz, Susanne, and Alexander Coppock.
    2023. “What Have We Learned about Gender from Candidate Choice Experiments? A Meta-Analysis of Sixty-Seven Factorial Survey Experiments.” The Journal of Politics 84 (2): 655–68. <https://doi.org/10.1086/716290>. Pedersen, Rasmus T., Jens Olav Dahlgaard, and Manuele Citi. 2019. “Voter Reactions to Candidate Background Characteristics Depend on Candidate Policy Positions.” Electoral Studies 61 (October):102066. https://doi.org/10.1016/j.electstud.2019.102066.

(7) Eg: Schneider, Howard.
    2024. “Trump Wants to Compare Now to Four Years Ago. Here’s What It Looks like \| Reuters.” Reuters, October 30, 2024. <https://www.reuters.com/world/us/does-trump-really-want-compare-now-four-years-ago-2024-10-30/>.

(8) Eg: Morris, G. Elliott. 2024. “Who Is Favored To Win The 2024 Presidential Election?” FiveThirtyEight. June 11, 2024. https://projects.fivethirtyeight.com/2024-election-forecast/.

(9) Shah, Ronak.
    2021. “Answer to ‘How Can I Add a Row with the Mean of Each Numeric Column.’” Stack Overflow. <https://stackoverflow.com/a/69264173>.
Model Summary Help Page; “Gross Domestic Product \| U.S. Bureau of Economic Analysis (BEA).” n.d. Accessed November 1, 2024. <https://www.bea.gov/data/gdp/gross-domestic-product>.; Kosourova, Elena.
    2022. “How to Append Rows to a Data Frame in R (with 7 Code Examples).” Dataquest. July 28, 2022. <https://www.dataquest.io/blog/append-to-dataframe-in-r/>.

(10) “Code Book Master 1996 2024 Election Voting Re.Docx.” n.d. Google Docs. Accessed November 2, 2024. https://docs.google.com/document/u/1/d/1XeoTI0GDit2X0KxlZ0kwX0oVSkOS-19P/edit?usp=drive_web&ouid=118424910218509828098&rtpof=true&usp=embed_facebook.
Index, Cost of Voting. n.d. “Cost of Voting Index.” Cost of Voting Index. Accessed November 2, 2024. https://costofvotingindex.com/.

(11)  Rubin, April. 2023. “Supreme Court Ideology Continues to Lean Conservative, New Data Shows.” Axios. July 3, 2023. https://www.axios.com/2023/07/03/supreme-court-justices-political-ideology-chart.

(12) Eg: Grimmer, Justin, Eitan Hersh, Marc Meredith, Jonathan Mummolo, and Clayton Nall. 2018. “Obstacles to Estimating Voter ID Laws’ Effect on Turnout.” The Journal of Politics 80 (3): 1045–51.; Foley, Jordan M, Michael W Wagner, Ceri Hughes, Jiyoun Suk, Katherine J Cramer, Lewis A Friedland, and Dhavan V Shah. 2021. “Free and Fair? The Differential Experiences of Voting Barriers and Voting Policies in American Midterm Elections.” International Journal of Public Opinion Research 33 (3): 703–12. https://doi.org/10.1093/ijpor/edab009.
Thompson, Daniel M., Jennifer A. Wu, Jesse Yoder, and Andrew B. Hall. 2020. “Universal Vote-by-Mail Has No Impact on Partisan Turnout or Vote Share.” Proceedings of the National Academy of Sciences 117 (25): 14052–56. https://doi.org/10.1073/pnas.2007249117. 

(13) Eg: Badas, Alex, and Elizabeth Simas. 2022. “The Supreme Court as an Electoral Issue: Evidence from Three Studies.” Political Science Research and Methods 10 (1): 49–67. https://doi.org/10.1017/psrm.2021.20.
Chemerinsky, Erwin. 2024. “Opinion: How Much Will the Supreme Court Matter in the 2024 Election?” Los Angeles Times. October 6, 2024. https://www.latimes.com/opinion/story/2024-10-06/election-donald-trump-kamala-harris-supreme-court. Etzerodt, Søren Frank. 2024. “The Electoral Consequences of Abortion Politicization in the US.” European Journal of Politics and Gender, August, 1–5. https://doi.org/10.1332/25151088Y2024D000000049. Nadeem, Reem. 2024. “2. Issues and the 2024 Election.” Pew Research Center (blog). September 9, 2024. https://www.pewresearch.org/politics/2024/09/09/issues-and-the-2024-election/.

(14) Kriner, Douglas L., and Andrew Reeves. 2012. “The Influence of Federal Spending on Presidential Elections.” American Political Science Review 106 (2): 348–66. https://doi.org/10.1017/S0003055412000159.

(15) Sebastian. (2021) 2022. “Sebastianbahr/glmnetSE.” R. https://github.com/sebastianbahr/glmnetSE.; Bahr, Sebastian. 2021. “glmnetSE: Add Nonparametric Bootstrap SE to ‘glmnet’ for Selected Coefficients (No Shrinkage).” https://CRAN.R-project.org/package=glmnetSE. glmnetSE help page; Sebastian. (2021) 2022. “Sebastianbahr/glmnetSE.” R. https://github.com/sebastianbahr/glmnetSE.; Bahr, Sebastian. 2021. “glmnetSE: Add Nonparametric Bootstrap SE to ‘glmnet’ for Selected Coefficients (No Shrinkage).” https://CRAN.R-project.org/package=glmnetSE. glmnetSE help page

(16) Morris, G. Elliott. 2024. “Who Is Favored To Win The 2024 Presidential Election?” FiveThirtyEight. June 11, 2024. https://projects.fivethirtyeight.com/2024-election-forecast/.; Dardet, Matthew. 2024. “Week 8 - ElectionAnalytics2024 - Google Drive.” Presented at the GOV 1437 Lab, October 23. https://drive.google.com/drive/u/1/folders/1meFzvnodlH_v_wpfQiIJoZa7YWBBXH5U.
Morris, G. Elliott. 2024. “How 538’s 2024 Presidential Election Forecast Works.” ABC News. August 23, 2024. https://abcnews.go.com/538/538s-2024-presidential-election-forecast-works/story?id=113068753.

(17) Enos, Ryan. 2024. “Laws and Administration.” Presented at the Election Analytics Discussion 9, October 29.

(18) Dardet, Matthew. 2024. “Week 8 - ElectionAnalytics2024 - Google Drive.” Presented at the GOV 1437 Lab, October 23. https://drive.google.com/drive/u/1/folders/1meFzvnodlH_v_wpfQiIJoZa7YWBBXH5U.
Morris, G. Elliott. 2024. “How 538’s 2024 Presidential Election Forecast Works.” ABC News. August 23, 2024. https://abcnews.go.com/538/538s-2024-presidential-election-forecast-works/story?id=113068753.
Silver, Nate. 2024. “2024 Presidential Election Model Methodology Update.” June 26, 2024. https://www.natesilver.net/p/model-methodology-2024. “About the PollyVote.” n.d. PollyVote (blog). Accessed November 3, 2024. https://www.pollyvote.com/about/.


(19) Shaw, Daron R., and John R. Petrocik. 2020. The Turnout Myth: Voting Rates and Partisan Outcomes in American National Elections. Oxford University Press.

(20) Eg: Axelrod, Tal. 2024. “Third-Party Candidates Could Be Swing-State Spoilers Even after Intense Democrat Efforts.” ABC News. November 1, 2024. https://abcnews.go.com/Politics/democrats-hard-block-party-candidates-spoilers/story?id=115273808.
Bouranova, Alene. 2024. “Is Voting for a Third-Party Candidate Effective or Is It a Wasted Vote? (And Other Third-Party Questions).” Boston University. October 28, 2024. https://www.bu.edu/articles/2024/is-voting-third-party-a-wasted-vote/. Morris, G. Elliott. 2024. “Who Is Favored To Win The 2024 Presidential Election?” FiveThirtyEight. June 11, 2024. https://projects.fivethirtyeight.com/2024-election-forecast/.

(21) Kim, Seo-young Silvia, and Jan Zilinsky. 2024. “Division Does Not Imply Predictability: Demographics Continue to Reveal Little About Voting and Partisanship.” Political Behavior 46 (1): 67–87. https://doi.org/10.1007/s11109-022-09816-z.

(22) Kalla, Joshua L., and David E. Broockman. 2018. “The Minimal Persuasive Effects of Campaign Contact in General Elections: Evidence from 49 Field Experiments.” American Political Science Review 112 (1): 148–66. https://doi.org/10.1017/S0003055417000363.

(23) Personal conversation, Jamie Liu, November 1, 2024

(24) Eg: Javanmard, Adel, and Andrea Montanari. 2014. “Conﬁdence Intervals and Hypothesis Testing for High-Dimensional Regression.” Journal of Machine Learning Research 15:2869–2909. EdM. 2020. “Answer to ‘How Do I Calculate Confidence Intervals on an Elastic Net Regression in R.’” Cross Validated. https://stats.stackexchange.com/a/478188.
ilanman. 2016. “Answer to ‘Confidence Intervals for Ridge Regression.’” Stack Overflow. https://stackoverflow.com/a/40509534.

(25) “RPubs - Linear Regression Confidence and Prediction Intervals.” n.d. Accessed October 26, 2024. https://rpubs.com/aaronsc32/regression-confidence-prediction-intervals.

# Data Sources

All data sources are provided by GOV 1372 course staff

Popular Vote Datasets

-   National Popular Vote Data from Wikipedia, Abramowitz (2020), Abramowitz (2020) replication data, and manual changes

-   State Popular Vote Data from MIT elections project, Wikipedia, and manual editing

-   Additional data from Politico and Wall Street Journal for Maine and Nebraska District 2 added to test dataset to enable lagged predictions

Economic Data

-   FRED Data from St. Louis FRED (appended with data from BEA and Brookings for 2023 GDP growth and Unemployment Figures)

-   Grants Data from Kriner and Reeves (2015) replication data

Polling Data

-   State Polls from FiveThirtyEight poll averages and preprocessing

Elector Data
- National Archives and Wikipedia, augmented with 2024 data for Nebraska and Maine districts from FiveThirtyEight

Cost of Voting Index
- Created by Michael Pomante II, but also generously facilitated by GOV 1372 course staff

Turnout
- Calculated from the Current Population Survey by Michael McDonald's US Elections Project

Data sources for Supreme Court cases are unknown, but were generously provided by the GOV 1372 course staff. However, I append the Supreme Court data with a metric of how the Supreme Court's lean changed over time with data from Axios (Rubin, April. 2023. “Supreme Court Ideology Continues to Lean Conservative, New Data Shows.” Axios. July 3, 2023. https://www.axios.com/2023/07/03/supreme-court-justices-political-ideology-chart.


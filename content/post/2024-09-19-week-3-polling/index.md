---
title: Week 3 - Polling
author: Shriya Yarlagadda
date: '2024-09-19'
slug: week-3-polling
categories: []
tags: []
---

In this week’s post, we focus on analyzing polling data, attempting to understand how they can best predict election outcomes. My thanks again to Matthew Dardet for his generous starter code.

For the purpose of this analysis, we focus on polling data from FiveThirtyEight. We began by visualizing the available data from the past several elections, understanding how polling data changes relative to the actual election outcome.

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-2-1.png" width="672" />

This data shows the polling averages at various stages of the election, benchmarked against the actual vote share earned by each candidate during that year’s election (horizontal lines). This is very likely affected by events occurring during the election cycle and each campaign’s response to them. For example, we see a substantial decline in support for Donald Trump around June 2020 - perhaps corresponding to the murder of George Floyd (1).

However, it is interesting to see if election forecasts made using polling data in the few weeks prior to the election are necessarily more predictive of the final outcomes than those considering prior weeks. Some, such Tien and Lewis-Beck, claim that “short-view forecasts,” which solely rely on polling data, especially in the weeks prior to the election, tend to be inaccurate (2). While some of these charts above show relatively accurate November predictions (eg: Biden’s polling in 2020), many others are very inaccurate. For example, polling about 15 weeks before the election better predicted Trump’s 2016 vote share than polling in the weeks immediately prior.

To test the accuracy of November polls, we computed several regressions of November polling averages on actual election outcomes between 1968 and 2020 (we have data as early as 1948, but we drop earlier years given that we do not have polling data from FiveThirtyEight from 1948-1964). I calculated three separate regressions, highlighted in the table below, which model predictions for only Democratic candidates, only Republicans, and both parties respectively.

<!-- preamble start -->
&#10;    <script>
      function styleCell_2yfc6amic90h7lc747pg(i, j, css_id) {
        var table = document.getElementById("tinytable_2yfc6amic90h7lc747pg");
        table.rows[i].cells[j].classList.add(css_id);
      }
      function insertSpanRow(i, colspan, content) {
        var table = document.getElementById('tinytable_2yfc6amic90h7lc747pg');
        var newRow = table.insertRow(i);
        var newCell = newRow.insertCell(0);
        newCell.setAttribute("colspan", colspan);
        // newCell.innerText = content;
        // this may be unsafe, but innerText does not interpret <br>
        newCell.innerHTML = content;
      }
      function spanCell_2yfc6amic90h7lc747pg(i, j, rowspan, colspan) {
        var table = document.getElementById("tinytable_2yfc6amic90h7lc747pg");
        const targetRow = table.rows[i];
        const targetCell = targetRow.cells[j];
        for (let r = 0; r < rowspan; r++) {
          // Only start deleting cells to the right for the first row (r == 0)
          if (r === 0) {
            // Delete cells to the right of the target cell in the first row
            for (let c = colspan - 1; c > 0; c--) {
              if (table.rows[i + r].cells[j + c]) {
                table.rows[i + r].deleteCell(j + c);
              }
            }
          }
          // For rows below the first, delete starting from the target column
          if (r > 0) {
            for (let c = colspan - 1; c >= 0; c--) {
              if (table.rows[i + r] && table.rows[i + r].cells[j]) {
                table.rows[i + r].deleteCell(j);
              }
            }
          }
        }
        // Set rowspan and colspan of the target cell
        targetCell.rowSpan = rowspan;
        targetCell.colSpan = colspan;
      }
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(0, 0, 'tinytable_css_idqlzkv9pvc9rfmjmtwkdc') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(0, 1, 'tinytable_css_id45zo9d5p2nb8n5vcqkpy') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(0, 2, 'tinytable_css_id45zo9d5p2nb8n5vcqkpy') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(0, 3, 'tinytable_css_id45zo9d5p2nb8n5vcqkpy') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(1, 0, 'tinytable_css_idj2ih8u8fjuth8g5avsqi') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(1, 1, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(1, 2, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(1, 3, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(2, 0, 'tinytable_css_idj2ih8u8fjuth8g5avsqi') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(2, 1, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(2, 2, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(2, 3, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(3, 0, 'tinytable_css_idj2ih8u8fjuth8g5avsqi') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(3, 1, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(3, 2, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(3, 3, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(4, 0, 'tinytable_css_idxpqtejct8p1sxy2swnmz') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(4, 1, 'tinytable_css_ida0s5vtntyqhwlepdgvys') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(4, 2, 'tinytable_css_ida0s5vtntyqhwlepdgvys') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(4, 3, 'tinytable_css_ida0s5vtntyqhwlepdgvys') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(5, 0, 'tinytable_css_idj2ih8u8fjuth8g5avsqi') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(5, 1, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(5, 2, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(5, 3, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(6, 0, 'tinytable_css_idj2ih8u8fjuth8g5avsqi') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(6, 1, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(6, 2, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(6, 3, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(7, 0, 'tinytable_css_idj2ih8u8fjuth8g5avsqi') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(7, 1, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(7, 2, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(7, 3, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(8, 0, 'tinytable_css_idj2ih8u8fjuth8g5avsqi') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(8, 1, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(8, 2, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(8, 3, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(9, 0, 'tinytable_css_idj2ih8u8fjuth8g5avsqi') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(9, 1, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(9, 2, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(9, 3, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(10, 0, 'tinytable_css_idj2ih8u8fjuth8g5avsqi') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(10, 1, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(10, 2, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(10, 3, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(11, 0, 'tinytable_css_idj2ih8u8fjuth8g5avsqi') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(11, 1, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(11, 2, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
window.addEventListener('load', function () { styleCell_2yfc6amic90h7lc747pg(11, 3, 'tinytable_css_idha2ae1uqk0wm1pr75ofp') })
    </script>
&#10;    <style>
    .table td.tinytable_css_idqlzkv9pvc9rfmjmtwkdc, .table th.tinytable_css_idqlzkv9pvc9rfmjmtwkdc {  text-align: left;  border-bottom: solid 0.1em #d3d8dc; }
    .table td.tinytable_css_id45zo9d5p2nb8n5vcqkpy, .table th.tinytable_css_id45zo9d5p2nb8n5vcqkpy {  text-align: center;  border-bottom: solid 0.1em #d3d8dc; }
    .table td.tinytable_css_idj2ih8u8fjuth8g5avsqi, .table th.tinytable_css_idj2ih8u8fjuth8g5avsqi {  text-align: left; }
    .table td.tinytable_css_idha2ae1uqk0wm1pr75ofp, .table th.tinytable_css_idha2ae1uqk0wm1pr75ofp {  text-align: center; }
    .table td.tinytable_css_idxpqtejct8p1sxy2swnmz, .table th.tinytable_css_idxpqtejct8p1sxy2swnmz {  border-bottom: solid 0.05em black;  text-align: left; }
    .table td.tinytable_css_ida0s5vtntyqhwlepdgvys, .table th.tinytable_css_ida0s5vtntyqhwlepdgvys {  border-bottom: solid 0.05em black;  text-align: center; }
    </style>
    <div class="container">
      <table class="table table-borderless" id="tinytable_2yfc6amic90h7lc747pg" style="width: auto; margin-left: auto; margin-right: auto;" data-quarto-disable-processing='true'>
        <thead>
        &#10;              <tr>
                <th scope="col"> </th>
                <th scope="col">Democrats Only</th>
                <th scope="col">Republicans Only</th>
                <th scope="col">All Candidates</th>
              </tr>
        </thead>
        &#10;        <tbody>
                <tr>
                  <td>(Intercept)</td>
                  <td>33.713   </td>
                  <td>28.169   </td>
                  <td>30.642    </td>
                </tr>
                <tr>
                  <td>           </td>
                  <td>(0.468)  </td>
                  <td>(0.416)  </td>
                  <td>(0.319)   </td>
                </tr>
                <tr>
                  <td>final_poll </td>
                  <td>0.355    </td>
                  <td>0.507    </td>
                  <td>0.439     </td>
                </tr>
                <tr>
                  <td>           </td>
                  <td>(0.011)  </td>
                  <td>(0.009)  </td>
                  <td>(0.007)   </td>
                </tr>
                <tr>
                  <td>Num.Obs.   </td>
                  <td>3491     </td>
                  <td>3491     </td>
                  <td>6982      </td>
                </tr>
                <tr>
                  <td>R2         </td>
                  <td>0.241    </td>
                  <td>0.467    </td>
                  <td>0.351     </td>
                </tr>
                <tr>
                  <td>R2 Adj.    </td>
                  <td>0.240    </td>
                  <td>0.467    </td>
                  <td>0.351     </td>
                </tr>
                <tr>
                  <td>AIC        </td>
                  <td>19837.9  </td>
                  <td>18603.9  </td>
                  <td>38816.5   </td>
                </tr>
                <tr>
                  <td>BIC        </td>
                  <td>19856.4  </td>
                  <td>18622.4  </td>
                  <td>38837.0   </td>
                </tr>
                <tr>
                  <td>Log.Lik.   </td>
                  <td>-9915.945</td>
                  <td>-9298.944</td>
                  <td>-19405.234</td>
                </tr>
                <tr>
                  <td>RMSE       </td>
                  <td>4.14     </td>
                  <td>3.47     </td>
                  <td>3.90      </td>
                </tr>
        </tbody>
      </table>
    </div>
<!-- hack to avoid NA insertion in last line -->

Given that the Republican only model has an R^2 value of 0.727 while the Democrat only model has an R^2 value of 0.665 (with the combined model being in between), it appears that polling data from FiveThirtyEight has, on average, been more predictive of Republican outcomes. However, I also wanted to see if the relationship may have been skewed by earlier polling data, which was likely less accurate. To explore this, I wanted to see if earlier polls tended to be more inaccurate than more recent ones, starting with a scatterplot.

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-4-1.png" width="672" />

This scatterplot, which includes a line demonstrating perfect poll prediction, shows that most November polls are somewhat inaccurate, often underpredicting candidate performance. However, given that it didn’t clearly demonstrate trends in performance over the years, I calculated the years/candidates with the lowest November prediction error, including them in the table below.

| Year | Party |     Candidate      | Two-Party Vote Share | Final Poll Prediction of Vote Share | Prediction Error |
|:----:|:-----:|:------------------:|:--------------------:|:-----------------------------------:|:----------------:|
| 2012 |  REP  |    Mitt Romney     |        48.08         |                48.08                |       0.00       |
| 2004 |  DEM  |     John Kerry     |        48.73         |                48.74                |       0.01       |
| 2008 |  REP  |    John McCain     |        46.23         |                46.21                |      -0.02       |
| 2012 |  REP  |    Mitt Romney     |        48.08         |                48.07                |      -0.02       |
| 2008 |  REP  |    John McCain     |        46.23         |                46.25                |       0.02       |
| 2020 |  DEM  |         NA         |        52.27         |                52.25                |      -0.02       |
| 2012 |  REP  |    Mitt Romney     |        48.08         |                48.05                |      -0.03       |
| 2012 |  REP  |    Mitt Romney     |        48.08         |                48.12                |       0.04       |
| 1988 |  DEM  | Michael S. Dukakis |        46.17         |                46.13                |      -0.04       |
| 2012 |  REP  |    Mitt Romney     |        48.08         |                48.04                |      -0.04       |

This shows two interesting conclusions. First, all of the closest predictions have underpredicted candidate performance, showing a similar conclusion to the scatterplot. But second, and more relevantly, this tentatively suggests that recent polls haven’t necessarily been more successful. Of course, we cannot make a causal argument from just this data and many recent years make up our top 10, polling from 1968, the earliest year in our dataset, makes our top 10. This may lend credence to the argument that there are certain “fundamentals” that can help predict voter performance, regardless of data accuracy and statistical/computing power that pollsters may have access to (2).

Keeping the relative inaccuracy of only using November polling to predict outcomes in mind, we also wanted to explore if including polls at other times in an election cycle can result in better prediction outcomes. To do so, we used the regularization method of Elastic Net, identifying the most predictive weeks based on historical polling and election outcome data.

I trained this model using data from before 2020, evaluating it on the data from 2020. I did this because although we do have some data from 2024 and could reasonably make a prediction of this year’s election using our polling-based model, the fact that the Democratic candidate changed midway through the year may reduce the likelihood of our model (which is largely trained on elections that did have a similar shift).

| Prediction Error - Democratic Party (2020) | Prediction Error - Republican Party (2020) |
|:------------------------------------------:|:------------------------------------------:|
|                  2.119166                  |                 0.5729736                  |

Our model predicted that, based on polling trends from previous years, Biden would earn 54.4 % of the two-party popular vote, while Trump would earn 48.3% in 2020. While these predictions were slightly high for both candidates, the poll was off by over 2 percentage points for Biden. On one hand, this may be due to the substantial variations between this election and previous ones. However, it may lend further credence to the earlier point that polls tend to overpredict candidate performance. Furthermore, it aligns with our earlier finding (using only November polling) that election forecasts tend to more accurately predict outcomes for Republican candidates.

Given these findings, it is interesting to compare the perspectives that two major pollsters involved with FiveThirtyEight – Nate Silver and G. Elliot Morris – have proposed regarding election forecasting, an *extension* of our previous analytical work.

In a June 2024 article (5), Silver highlights the changes in his 2024 prediction relative to his 2020 predictions. In this, he seems to focus on making minor tweaks to his previous model, saying that he “tend\[s\] to be conservative about making changes to the election models. He appears to focus on very broad factors that affect election outcomes like party level turnout and incumbency. However, in an article released around the same time (6), Morris encourages considering the fundamentals, but takes a different perspective, considering, for example”the rates of change of these indicators.” In doing so, he also delves into greater specificity than Silver, observing characteristics like state effects on neighbors, seeming to stray away from a strict focus on “fundamentals.”

# Citations

1.  Silverstein, Jason. “The Global Impact of George Floyd: How Black Lives Matter Protests Shaped Movements around the World - CBS News,” June 4, 2021. https://www.cbsnews.com/news/george-floyd-black-lives-matter-impact/.

2.  Tien, Charles, and Michael Lewis-Beck. “Evaluating the Long-View Forecasting Models of the 2016 Election.” OUPblog, January 11, 2017. https://blog.oup.com/2017/01/forecasting-models-2016-election/.

3.  chemdork123. “Answer to ‘Change Scale on X Axis in Ggplot in R.’” Stack Overflow, July 20, 2020. https://stackoverflow.com/a/63003636.

4.  Posit Community. “Add X=y Geom_abline to Ggplot - General,” June 1, 2019. https://forum.posit.co/t/add-x-y-geom-abline-to-ggplot/32154.

5.  Silver, Nate. “2024 Presidential Election Model Methodology Update,” June 26, 2024. https://www.natesilver.net/p/model-methodology-2024.

6.  Morris, G. Elliott. “How 538’s 2024 Presidential Election Forecast Works.” ABC News, June 11, 2024. https://abcnews.go.com/538/538s-2024-presidential-election-forecast-works/story?id=110867585.

7.  GeeksforGeeks. “How to Create Tables in R?,” December 16, 2021. https://www.geeksforgeeks.org/how-to-create-tables-in-r/.

8.  “Build a Data Frame — Tibble.” Accessed September 22, 2024. https://tibble.tidyverse.org/reference/tibble.html.

9.  Daniel. “Answer to ‘Reverse the Scale of the x Axis in a Plot.’” Stack Overflow, March 28, 2019. https://stackoverflow.com/a/55390320.

Help documents for Model Summary, Top N, Slice_Max, Abs (Absolute Value), Geom_vline, Left/Right/Full Join, Linetype, kbl

# Data Sources

Poll Predictions from FiveThirtyEight and National Election Data (both provided by course)

# E-Sports: EDA of the LCS 2019 Tournament

## Contents
* [Background](#backgr)
* [Data Collection](#collect)
* [Results](#result)
  * [Continuous factors that affect a win or loss](#cont)
  * [Categorical factors that affect a win or loss](#categ)
  * [Pairwise relationships between factors](#pair)
* [Conclusion](#concl)
## <a name="backgr"></a> Background

The League Championship Series (LCS) 2019 is the annual tournament for the popular online game League of Legends (LoL), made by Riot Games.

I have been interested in how this game is played at a professional level, and so I believe this is an opportunity to not only learn more about it, but a way to improve my own gameplay also.

We conduct exploratory data analysis for post-game match data of the 2019 LCS tournament, looking into which variables significantly affect a match outcome. We also investigate any other relationships between variables.

## <a name="collect"></a> Data Collection

A LCS 2019 dataset was used from http://oracleselixir.com/match-data/, containing match data of all games during the tourney.

Also provided is a dictionary of terms used in the dataset: http://oracleselixir.com/match-data/match-data-dictionary/.
As a result, there may be many terms and jargon, specific to this game used in this report.


## <a name="result"></a> Results
We observe the distribution of game length of the 119 matches played during the tourney. We see that the majority of games are between 25 and 35 minutes, with less greater than 35 minutes, and only a few beyond 50 minutes.

![alt text](https://user-images.githubusercontent.com/60940406/89083243-526b5400-d388-11ea-99dc-46e36acab58c.png)

To investigate the effect of factors on a victory or loss, we will plot many correlation plots. The outcome variable is the column 'result' (1 = win, 0 = loss).

We look at Continuous and Categorical variables:

| Continuous    | Categorical   |
| ------------- |:-------------:|
| teamkills     | side |
| teamdeaths     | fb      |
| dmgtochamps   | fd     |
| totalgold  | fbaron      |
| wpm   | ft      |
| cspm   | herald     |
| teamdragkills   |      |
| visionwards   |       |
| wardkills  |       |


### <a name="cont"></a> Continuous factors that affect a win or loss

![alt text](https://user-images.githubusercontent.com/60940406/89083269-6616ba80-d388-11ea-9ffa-570974814eb3.png)

From these boxplots, we are able to grasp the distribution of the data points.

Firstly, there appears to be some outliers in many boxplot diagrams. However, it is not a good choice to remove these outliers since these data points are unlikely to be incorrect data points. Due to the nature of the data, it is likely that any outliers are just data points from the extremity case of matches. This case is different to outliers where the data are measurements of some unit, and were incorrectly measured, for example.

Generally, the boxplots show distributions of data that we are likely to expect. For instance, having a larger number of team gold or team kills increases the chance of victory. Many of these plots are like this, but the team kills (and team deaths) variable seems to have the most impact so far (out of the 9 variables we are looking at). This is due to the median of one boxplot passing the upper/lower quartile range of the other.

Another interesting result is how some variables do not seem to affect a win or loss, despite it seeming likely to affect it. This is the case with wpm, visionwards and wardkills. One reason for the absence of a relationship is due to those factors being fairly weak, when compared to factors such as team kills. From the boxplot, it seems as though both teams will have a similar frequency of the variable, and hence, not affect the result of a win or loss much. The lower frequency data points are likely to just be matches which are of short length.


### <a name="categ"></a> Categorical factors that affect a win or loss

And for categorical variables, we use countplots.
Let "W/L" = "Win/Loss"

![alt text](https://user-images.githubusercontent.com/60940406/89083274-6a42d800-d388-11ea-8e46-9922e2bd70ed.png)

From these results, it is as expected that the side of the map affects the result of a victory or loss very little. It is evenly distributed, and offset by a little, likely due to the low number of matches (119).

The other bar charts are as expected, but the chart with the first baron variable shows the most significant effect. From this, we can see that having first baron greatly increases the chance of victory. This is likely due to how effective having the baron buff is, resulting in many towers destroyed and eventually the nexus.

Furthermore, the team which destroys the first turret first also seems to be more likely to win. This is unexpected, since the first turret being destroyed does not seem to have too much of an impact. Perhaps it is the gold bonus, morale boost, or a synchronised herald push as a result, that contributes to other factors into a victory.

### <a name="pair"></a> Pairwise relationships between factors

Now that we have seen the effect of variables on a win loss, we can now investigate other aspects.
We look at whether there are any pairwise relationships between the continuous variables, using a heatmap.

![alt text](https://user-images.githubusercontent.com/60940406/89083276-6ca53200-d388-11ea-978f-a27ee5136d43.png)

This heatmaps indicates the relationship between the 9 variables chosen.

'teamdeaths' and 'cspm' have a negative relationship, which is as expected, since farming creeps consistently at such a high count implies less teamfighting. This means less team deaths. The low value between 'cspm' and 'teamkills' supports this idea of less teamfighting, since if there was more teamfighting, this value would be greater.

The other relationships with a large coefficient are mostly as expected, such as with 'dmgtochamps' and 'totalgold'. This is because a higher damage to champions implies more teamkills, and therefore more gold.

Other relationships to note are that 'wpm' and 'teamkills' being somewhat positive, along with 'wardkills' and 'teamkills' and 'visionwards' and 'teamkills'. This implies that having stronger vision control results in a greater number of kills.

![alt text](https://user-images.githubusercontent.com/60940406/89083281-6fa02280-d388-11ea-9e2f-5f3d94e1776a.png)

This relationship with a -0.58 coefficient shows a distribution that is fairly negatively correlated. This regression line, however, is just used to hint this negative relationship (the line does not seem fit the data very well and therefore is not representative of it).

## <a name="concl"></a> Conclusion

In general, many of the relationships found were as expected, except for some findings. The interesting relationships are the the "first turret" and "result" relationship, and the overall vision control relationships.

We had restricted our analysis to team statistics for this report. One of the main reasons were that a lot of individual player statistics are readily available online, and are largely known. This is also the case with the champions played, having their pick rate, ban rate, and win rate analysed. So, by focusing on team statistics, we were able to find more interesting and lesser known results.

One limitation of our findings was that since there only 119 games recorded during this LCS 2019 tourney, the relationships discovered are not reliable, due to the low sample size.

Another limitation, yet less significant, is the patch no. of this game (9.19). This means that the relationships found may be affected by this specific patch, but it is likely that it does not affect this much.

The implications of our found relationships are mainly only applicable to pro play, and hence, not applicable to games in general. This is due to the games being only from a world championship level.


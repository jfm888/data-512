John Mahoney\
Data 512\
Project Proposal\

# Analysis of 2019-20 NBA Season

### Motivation
The 2019-20 NBA season was the longest in history at 377 days. Due to the Covid-19 pandemic, on March 11 the 2019-20 NBA regular season was suspended(later ruled concluded) with most teams having completed only about 80% of their scheduled regular season games (82 games is standard). Almost five months later the leading 22 teams met to play a further 8 games to determine which 16 teams would continue to the playoffs and what the playoff seeding would be. These eight games as well as the playoffs and the championship games were played in the NBA Bubble( also called the Disney Bubble), an isolated part of Walt Disney World in Orlando Florida. This season is incredibly interesting in many ways as it begins to answer real questions about factors involved in competitive sports. These questions include: 

* What is the effect of a reduced regular season?
* Five months between regular season and playoffs may allow for players to recover from injuries, what effect does player injuries have on a playoff performance?
* During the regular season players traveled for games as usual, but in the NBA Bubble no teams traveled. What is the effect of eliminating the home-team vs. away-team categories?
* There were no fans in the Bubble, what role do fans play in team performance?
* Players were quarantined with few other people, could isolation be a factor in player and team performance?

There are many possible questions but they generally fall under the heading of studying possible effects of various factors on relative player performance, which inturn, affects team performance. There has never been an NBA season like the 2019-20 season, and by studying it we can begin to answer some of the most difficult questions in sports. The goal of this project is to use the 2019-20 NBA season to try to better understand what influences basketball team performance.

### Data

The most official basketball data is from the NBA itself, and our first preference is to use this data. These data are available for viewing on the [NBA’s website](https://www.nba.com/stats/ "NBA stats") however, there is no official API for downloading this data. To get this official NBA data we must use a third party python package [NBA_py](https://github.com/seemethere/nba_py "NBA_py github") to scrape NBA pages and output a json file. To answer interesting questions about the 2019-20 season we will likely need data reflecting regular season performance (team and player), playoff performance(team and player) as well as data from past seasons to use as comparison. [Dan Weston](https://medium.com/@dwatson828) has a great NBA sports analytics blog [Hardwood Convergence](https://medium.com/hardwood-convergence) where he covers how to use the NBA_py package; we will use code from Dan's [tutorial](https://medium.com/hardwood-convergence/move-over-scraping-pulling-nba-data-with-nba-py-3d68e621ba1) to help us with the NBA data.

Unfortunately, I have not yet been able to get the NBA_py package working, so we must proceed with existing data sets. [Basketball-Reference](https://www.basketball-reference.com/leagues/NBA_2020_games.html) is an excellent source for data, and the data is freely available for download and use as long as Basketball-Reference is mentioned as the source. I have collected the following datasets from [Basketball-Reference](https://www.basketball-reference.com/leagues/NBA_2020_games.html) and provided them in the Github Repo with an MIT License:

* 2019-20 NBA Regular Season Schedule
* 2019-20 NBA Playoff Schedule
* 2019-20 NBA Regular Season Summary
* 2019-20 NBA Playoff Summary
* 2019-20 NBA Regular Season Misc (a worksheet in the Regular Season Summary workbook)
* 2019-20 NBA Playoff Misc (a worksheet in the Playoff Summary workbook)


The above datasets are Excel files of tables downloaded from Basketball-Reference. The Schedule datasets contain a schedule of games and final scores. Each tuple contains: Date, Start Time - Eastern, Visiting Team, Points Scored, Home Team, Points Scored. The Summary datasets are very wide (25 columns) and contain information about in-game performance on a per-game basis averaged over either the regular season or the playoffs. I won't list every feature as there are many, but the tuples in the Summary dataset include: Field Goal Percentage (FG%) - percentage of 2pt or 3pt shots made; Free Throw Percentage (FT%); Offensive Rebounds(per game); and Assists - passes that directly precede a made basket. The last datasets are the "2019-20 NBA Regular Season Misc" and 2019-20 NBA Playoff Misc'' contain more advanced team statistics such as: eFG% - effective Field Goal Percentage - which accounts for the fact that 3pt shots are more valuable than 2pt shots; Ortg - Offensive Rating - points scored per 100 possessions; and Pace - Pace Factor - which is an estimate of the number of possessions per 48 minutes by a team. These datasets will be used to draw comparisons between regular season performance and playoff performance on a per team basis. Lastly, there are no ethical considerations to using this data, as no part of the data contains sensitive information, or anything that is not a matter of public record. All of this data is freely available and based solely on the public performance of professional basketball teams. 

### Unknowns and Dependencies

As I write this, there is nothing to prevent my ability to complete this project by the end of the quarter. I have data, I have questions about the data and I have the time to work. I may not get conclusive answers to the questions asked, but I should be able to do the work.

### Research Questions and Hypotheses

Question 1: Is playing only 75% of a season enough to determine the best teams to send to the playoffs?

Hypothesis 1: The last 25% of regular season play has no impact on playoff team selection.

Question Rationale: The NBA regular season is 82 games long, the 2019-20 season was only about 62-65 games long. I believe that the reduced season is enough to determine the best playoff teams, which is what the NBA believed as it did not require extra regular season games to select teams. If it turns out there is a difference between regular season and playoff season play I follow up questions may include:

* Is the playoff champion team always included in the playoffs bound teams once 75% of the season is over?
* What is the minimum number of games needed to determine the best playoff teams?

Question 2: Does taking a long break between regular and playoff seasons affect team performance?

Hypothesis 2: The long break has no impact on team performance, playoff performance is consistent with regular season performance.

Question Rationale: There was a five month break between regular season and playoff season play. This should be enough time for players to recover from injuries sustained during the regular season. Additionally this is enough time for teams to make adjustments on offense and defense in order to be more competitive. When considering these factors I suspect the long break will improve the competitiveness of teams resulting in a difference between regular season and playoff season play. If there is a difference in playoff and regular season play, follow up questions may include:

* Does not traveling (time and possible altitude change between locations) have an impact on player performance?
* Does the isolation of players (no fans at games, and living in a quarantined hotel) impact player performance?

### Background and Related Work

The 2019-20 season has been unique and has rightly been the subject of a lot of analysis and reporting. For a description of the lives of players inside the Bubble [Sam Anderson](https://www.nytimes.com/2020/09/30/magazine/nba-bubble.html) [1] wrote a great article for the New York times. This article is a fascinating account of the stress players feel of being in the Bubble, and is some of the motivation for my second question as well as possible follow up questions. The work by [Simon Spichak](https://towardsdatascience.com/the-basketball-in-the-bubble-cfec7976574b)[2] dispels the idea that travel has an effect on team performance however, Spichak wrote this article before the start of the 2019-20 playoffs. Living and playing in the Bubble is unlike traditional away games in that players are so much more isolated (from friends, family and even fans at games) it is possible this does have an affect on team performance. My interest in the length of the regular season stems from the fact that the NBA left the remaining games of the 2019-20 season unplayed. If these games were consequential they should have been played, but these games obviously were not played. The site FiveThirtyEight published a series of articles on  where teams which participated in the NBA playoff Bubble rank in regards to their likelihood of winning the championship. A particular article of this series discusses teams with a low probability of winning it all, "Teams Just Along for the Ride" by [Jared Dubin](https://fivethirtyeight.com/features/whos-who-in-the-nba-bubble-the-teams-just-along-for-the-ride/)[3]. The idea that teams who barely qualify for the playoffs may have a reduced chance of winning the championship could imply that the remaining 25% of games unplayed in the 2019-20 season may not be important.  Jared Dubin's articles suggest the teams with the highest percentage of regular season wins to losses also have the best chance of winning the championship, and these top teams have no need of additional regular season games. It's the teams that just barely didn't qualify that may want additional regular season games, and even if they were to qualify with the extra games, these teams would have only a small chance of beating the other teams. Sports analytics and the NBA Bubble in particular is a well-trod area of research, but despite much previous work I have not found satisfying answers to the questions I am interested in.

References:

1. Anderson, Sam. “What I Learned Inside the N.B.A. Bubble.” The New York Times, The New York Times, 30 Sept. 2020, www.nytimes.com/2020/09/30/magazine/nba-bubble.html.

2. Spichak, Simon. “The Basketball in the Bubble.” Medium, Towards Data Science, 29 July 2020, towardsdatascience.com/the-basketball-in-the-bubble-cfec7976574b.

3. Dubin, Jared. “Who's Who In The NBA Bubble: The Teams Just Along For The Ride.” FiveThirtyEight, FiveThirtyEight, 20 July 2020, fivethirtyeight.com/features/whos-who-in-the-nba-bubble-the-teams-just-along-for-the-ride/.

### Methodology

The work will generally consist of linear modeling to predict performance of teams and players (assuming performance is linear) and using t-tests to determine significance of results/hypothesis testing. For example in Research Question 1, I will use linear modeling to chart the performance of teams in the regular season. I will use these models to look for trends that may indicate a change in relative team ranking if more games were played. I would then use a t-test to determine if the results of this analysis are significant at a 95% confidence level. In similar fashion, for Question 2 I would use linear models to chart team performance in the playoffs and compare it to performance in the regular season, and use t-tests to check for significance. I'm assuming linearity as many articles, including Sipchak's[2], state the biggest factor in determining future wins is past wins. If the difficulty level of games does not increase as the season progresses, then the probability of a team winning the last 25% of the season may be the same as any other selection of games. In a linear model, this uncorrelation would be a straight line. If a team is improving relative to other teams over the course of the season, the line will not have a zero slope. In either situation, a linear model is useful as we could predict a result of playing the remaining 25% of games. During my analysis I may want to use other methods, but as it stands now, the only tools I'll certainly use are linear models and t-tests.

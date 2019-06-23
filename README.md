# NBA-Playoffs---Missingness-and-Hypothesis-Test

This project uses data from `basketball-reference.com` to ask questions about NBA players, who makes it to the playoffs.

# Summary of Findings


## Introduction
---
I am working with a dataset that contain's player statistics from each team in the NBA from 2012-2018. It contains the data of each player from their team, age, and all types of in-game statistics. My question relates to one position in particular, and how centers perform in the regular season compared to the playoffs. Before diving into my hypothesis test, I first joined the tables of regular season player data and playoff player data. Then I cleaned certain columns and added new columns that would be convenient for data and missingness analysis later on. I also selected certain columns to conduct data analysis and to find general trends across the years.

I was met with a few roadblocks, such as not having win data for each team during each season, or not considering enough statistics when testing to see if centers performed better in the playoffs. Overall, I was able to effectively clean my data and perform data analysis and hypothesis tests.



### Results of Cleaning and EDA:
---

First off, as I pulled the data from the url, I made each year's player data into separate dataframes, and appended a column to them that would clearly indicate which year each dataset came from. Then I appended each year's data into one table, for both regular season and playoffs. My next step was to join these two tables containing 6 years worth of data, and I differentiated the regular season and playoff by appending separate suffixes to their column names. I then saved them as local files so as to not repeatedly pull data from the website. I also made sure to do a left join, so that all the players in the regular season are included.

As I started cleaning the data, I dropped a few useless columns and reset the indices. I dropped the rows that contained column names, which were formed when appending the dataframes by rows. The most tedious part was changing all the corresponding column data types to either integer or floats, because they came in as strings but I needed integers to work with.

My data exploration starts with looking at the average field goal percentage by each position. I found that centers have the highest field goal percentage, at 52%, which is slightly higher than all other positions. This is most likely because centers take more high percentage shots like shots in the key or dunks.

Next, I looked the field goal percentage by team from during the regular season versus the playoffs. I found that only 4 teams had a higher field goal percentage in the playoffs than durin the regular season, which was not what I expected as usually teams play harder and better during the playoffs.

Finally, I looked at the total points scored by each team throughout the years. I found that each team increased their points made by around 2000 points through 6 years. This could be due to more teams shooting 3's and increasing their offensive game.

### Results of Missingness:
---
After examining both the regular season and playoffs datasets for 2012-2018 for missingness, there were two main sources of missingness. I found that the first major type of missingness is missing shot made/attempted percentages . When you examine the tables separately, these missing values are visible in the shot percentage columns. It includes field goal, 2 pointers, 3 pointers, free throws, and eFG, or effective field goal percentages. These missing percentages can be attributed to that certain players never took 3 pointers or free throwsduring the season, leading to a 0 for 0 shots made / attempted rate. Since any number divided by 0 is undefined, those values by default nan or missing. I did, however, consider that some players also had null shot percentages because they didn't play games that season, which evidently means they couldn't have taken any shots.

I found that the second type of missingness is the reason that not all teams make it to the playoffs. Only 16 of the 30 teams can make it to the playoffs each year. This fact accounts for a majority of the missing values in the joined table, since around half of the players couldn't make it into the playoffs. Since that player does not exist on the playoff roster, many of their stats such as games, types of shots made/attempted, and in game stats such as blocks and turnovers are all null. I considered that around the proportion of players missing is around the same to the proportion of teams that did not make the playoffs.

These were ultimately the two major types of missing data in this dataset. There were no permutation tests that were required. I assessed both the missing data as Missing at Random. The first type is MAR conditional on the shots attempted for that shot type. The second type is MAR conditional on the column that indicates whether or not they made it to the playoffs.

### Results of Hypothesis Test
---
I asked the question of whether or not centers overperform in the playoffs compared to the regular season. I arrived at this question because I thought centers go unnoticed when they don't make highlights, but they're still putting up big numbers. My null hypothesis stated that centers perform at a similar level in the playoffs versus the regular reason. My alternative hypothesis implied that centers performed better in the playoffs.

I created my test statistic of sampling 10 centers from both the regular season and playoff, and then calculating their difference in means. 

To simulate my hypothesis, I generated data under my null hypothesis 10000 times and calculated the difference of means for each sample. In the end, I found a p-value of 0.368, which is much higher than my significance level of 0.05. I concluded that I fail to reject the null hypothesis, and I could not find a correlation that centers perform better in the playoffs.


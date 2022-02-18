# Identifying Patterns in Video Game Sales

### Contents
1. [Objectives](https://github.com/SteveLewisUK/datascience_bootcamp_projects/blob/main/identifying_patterns_in_video_game_sales/README.md#objectives)
2. [Data](https://github.com/SteveLewisUK/datascience_bootcamp_projects/blob/main/identifying_patterns_in_video_game_sales/README.md#data)
3. [Method and Tools Used](https://github.com/SteveLewisUK/datascience_bootcamp_projects/tree/main/identifying_patterns_in_video_game_sales#method-and-tools-used)
4. [Conclusions](https://github.com/SteveLewisUK/datascience_bootcamp_projects/blob/main/identifying_patterns_in_video_game_sales/README.md#conclusions)<br />


### Objectives
The online store *Ice* sells video games worldwide. User and expert reviews, genres, platforms (e.g. Xbox or PlayStation) and historical data on game sales are available from open sources. The company wished to identify patterns that determine whether a game succeeds or not. This will allow it to spot potential big winners and plan advertising campaigns.

The objective of this project was to carry out a preliminary analysis of historical data on game sales. It is December 2016 and the company was planning a campaign for 2017.<br />


### Data
|**Feature** | **Description** |
|:---------------|:-----------------|
| Name  |     |
|Platform          |                          |
| Year_of_Release      |                     |
| Genre                |                     |
| NA_sales             | North American sales in USD million |
| EU_sales             | European sales in USD million       |
| JP_sales              | Sales in Japan in USD million      |
| Other_sales  |    Sales in other countries in USD million   |
| Critic_Score     |   Maximum of 100   |
| User_Score     |   Maximum of 10    |
| Rating     |  The Entertainment Software Rating Board (ESRB) evaluates a game's content and assigns an age-based rating such as Teen or Mature   |

There were 16,715 rows in the dataset.  Data for 2016 may be incomplete<br />


### Method and Tools Used
***Step 1***: Identifying null values and the distribution of variables; plotting variable distributions\
***Step 2***: Exploring strategies to deal with null values; removing rows where necessary. Creating new columns\
***Step 3***: Analysed the data as required: pivot tables with resetting index and automating plotting of multiple charts (line graphs, histograms, boxplots)\
***Step 4***: Plotted scatterplots and produced correlation matrix\
***Step 5***: Identified top genres bygeographical regionand produced pie charts\
***Step 5***: Hypothesis testing: 2 sided tests with data from two independent data sources (formulate null and alternative hypotheses).<br />


### Summary of Key Conclusions
- With the exception of the PS4 platform, the total sales of all platforms in the top 10 had sales approaching zero at the end of 2016. The life of a platform generally appeared to be between 6-10 years.
- The most profitable platforms at the end of 2016 were PS4 and XOne and the span of a game across all platforms is between 1-3 years
- The differences in sales by platform are significant: the average (median) annual sales was highest for the PS4 at around 100m USD, followed by the XOne at around 55m USD. Many platforms (including the PC, PSP, PSV, Wii, WiiU and X360) had average annual sales under 20m USD globally.
- There is a positive correlation between critic_score and total_sales of 0.406 but no correlation between user_score and total_sales. Critics' reviews do effect sales, but user reviews do not. 
- The most profitable genres are 'Action'. 'Sports' and 'Shooter'. The genres with the lowest sales are 'Puzzle', 'Adventure' and 'Strategy'.

#### International Research:
  
- The X360 is the most popular platform in North America and it is the 3rd most popular in the EU, however it does not rank in the top 5 in Japan. The PS2 is popular in all three territories, but the PS3 does not feature in the top 5 in Japan while it does in both North America and the EU. There are two platforms that appear in the top 5 in Japan (SNES and 3DS) which do not appear in the top 5 for North America and the EU Countries.
- In North America and Europe, Action, Sports and Shooter games are the 3 most popular. In Japan the most popular genre is 'Role-Playing' games which do not feature in the top 5 genres of either North America or Europe.
- Games with the rating 'E' rating (meaning 'Everyone; ie the content is suitable for all ages) are most popular in North America and Europe. In Japan this seems not to be the case as many games with no rating at all (which we have categorised as 'none' sell over 4 times more than games with an 'E' rating.)

#### Hypothesis Testing:

- I compared the average user ratings of the Xbox One and the PC platforms to test if they are the same. This was a 2 sided test with data from two independent data sources. I found the p-value to be very small, which meant that if the means of the two datasets were indeed the same, only around a 0.000004 of the values would have the same mean. That is, there is a very small probability of them randomly being the same. This probability is low enough to conclude that the null hypothesis can be rejected; that the average user scores of these two platforms are equal.
- I also compared the average user ratings for the Action and Sports genres to test if they are the same. This time the p-value (at 0.073) was greater than alpha, the critical statistical significance level. This means that if the means of the two datasets were indeed the same, 7.3% of the random samples would have the same mean. Given this, we cannot reject the null hypothesis that they are the same, ie they are probably not different.

# DSGA-1001_data_analysis_project1
DSGA-1001 Data Analysis Project 1: Analysis of movie ratings data set
<br>
This repository contains the code notebook and data used for this project as well as the results of our analysis.
* <em>IDS_Project1.ipynb</em> is Python notebook used.
* <em>movieReplicationSet.csv</em> is the movie ratings data used.
<br>

There are also a folder:<br>
* <em>Analysis plots</em> contains the plots used to show the results of the analysis.
<br>

# Analysis Report
**Question 1:** 
We want to first determine the two groups we are comparing: one group with more ratings and one group with less ratings. We first determine the number of ratings for each movie by counting the number of non-missing values, then calculating the median of the number of ratings. After doing so, we compare the number of ratings of each movie to the median that we found. If the number of ratings is higher than the median for a movie, we add it to the group with higher popularity, and the rest of the movies are added to the group with lower popularity. To test whether the higher popularity group is rated higher than the lower popularity group, we choose to use an one-tailed Mann-Whitney U test. Since we are looking at user ratings, it is inappropriate to reduce our dataset to its mean. Then, after performing a Kolmogorov-Smirnov(KS) test, we noticed that the distribution between the two groups are not very similar (with a D-value 0.194). Thus, we decided to choose our test statistic to be the median, which gives us the freedom to use data with almost any distribution or unit size, and choose to use a Mann-Whitney U test. The same reasoning applies to problem 1-8 in our report. In addition, since we are trying to determine whether more popular movies are rated higher instead of rated differently, we are doing an one-tailed Mann-Whitney U test. The test result shows a p-value of 0.000, allowing us to conclude that we can reject the null hypothesis and more popular movies are indeed rated higher than less popular movies.

![alt_text](https://github.com/sophiejuco/DSGA-1001_data_analysis_project1/blob/main/Analysis%20plots/plotQ1.png)

**Question 2:**
We want to determine the two groups we are comparing: one group with an earlier release year and one group with a later release year by first finding the years released for each movie, calculating the median, and comparing the years released for each movie with the median as we did for question 1. If the year released for a movie is newer than the median year, we add it to the newer group, and the rest of the movies are added to the older group. Similarly, we chose to use the Mann-Whitney U test. Since we are testing for difference rather than higher or lower, we do a two-tailed test. The result shows a p-value of 1.285e-6, allowing us to conclude that we can reject the null hypothesis and more popular movies are indeed rated higher than less popular movies.

**Question 3:**
The two groups we are testing here are: one group with ratings from male viewers and one group with ratings from female viewers. To do so, we first remove the missing data, then add ratings to the two groups based on the gender information provided. As we are using median as our test statistic and comparing two groups, we consider Mann-Whitney U test to be a reasonable choice. Here, since we are testing for difference, we want to do a two-tailed test. The test result gives us a p-value of 0.051, and therefore we can conclude that there is no strong evidence that the enjoyment of 'Shrek (2001)' is gendered. 

**Question 4:**
To find the proportion of movies rated differently by male and female viewers, we want to apply the same test as we used for the previous question to all movies listed. With the same reasoning, we choose to use a two-tailed Mann-Whitney U test on each of the movies. If the p-value is smaller than our chosen significance level 0.005 for a movie, we consider this movie to be rated differently and add it to our list. After testing all the movies, the list we keep contains 50 such movies in total, and therefore we conclude that the proportion of movies that are rated differently by male and female viewers is 0.125. 

**Question 5:**
To answer if people who are only children enjoy “The Lion King (1994)” more than people with siblings, we divided people who give rating to “The Lion King” into 2 groups: only children and with siblings. We remove all the NaN values in the movie rating. 151 are only children and 776 have siblings. An one-tailed Mann-Whitney U test was used. The test result shows a p-value of 0.98. Therefore we conclude there is no strong evidence that only children enjoy the movie ‘The Lion King (1994)’ more than people with siblings.

**Question 6:**
To see what proportion of movies exhibit an “only child effect” , we used a two-sided Mann-Whitney U test on each movie and grouped those with significant p-value (<0.005). 1.75% of movies exhibit an “only child effect”. 

**Question 7:**
Similar to problem 5, we divided people who give rating to “The Wolf of Wall Street (2013)” into 2 groups: watch movies alone and watch movies socially. Among the raters, 270 prefer to watch movies alone and 393 prefer to watch movies socially. An one-tailed Mann-Whitney U test was used. The test result shows a p-value of 0.943. Therefore we conclude there is no strong evidence that people who watch movies socially enjoy the movie ‘The Wolf of Wall Street (2013)’ more than people who watch movies alone.

**Question 8:**
To see what proportion of movies exhibit a “social watching effect” , we used a two-sided Mann-Whitney U test on each movie and grouped those with significant p-value (<0.005). 2.5% of movies exhibit a “social watching effect”. 

**Question 9:**
In order to find if the ratings distributions of “Home Alone (1998)” and “Finding Nemo (2003)” are different, the ratings data of the two movies was extracted from the original dataframe and then combined into one data frame where NaN values were removed row-wise so as to not accidentally confound on any superfans of one movie or the other. These data represent viewers who watched and rated both movies. In order to compare the distributions of the ratings of the two movies statistically, a Kolmogorov-Smirnow test was used. The KS test was used as it evaluates the similarity of two distributions of categorical data that is not reduced down to some aggregate of the data. The resulting p-value from this KS test was 2.20e-10 which is less than the alpha cutoff of 0.005. So, it can be concluded that there is a significant difference in the ratings distributions of “Home Alone (1998)” and “Finding Nemo (2003)” and we can reject the null hypothesis that the two movies have the same underlying distribution.

![alt_text]()


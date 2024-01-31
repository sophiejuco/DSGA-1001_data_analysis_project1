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

![alt_text]()

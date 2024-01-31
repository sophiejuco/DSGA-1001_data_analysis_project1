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

![alt_text](https://github.com/sophiejuco/DSGA-1001_data_analysis_project1/blob/main/Analysis%20plots/pltQ9.png)

**Question 10:**
 To assess which of the the franchises (“Star Wars”, “Harry Potter”, “The Matrix”, “Indiana Jones”, “Jurassic Park”, “Pirates of the Caribbean”, “Toy Story”, and/or “Batman”) are inconsistent in quality according to viewers, the ratings of all of the movies in a given franchise were tested on an ANOVA test. For each franchise, the ratings data of all the movies were extracted using the Pandas filter method with the key word(s) of each franchise as listed above. Once extracted, NaN values were removed row-wise so the data are consistent with viewers that watched and rated all the listed movies in a given franchise. This avoids the issue of confounding on viewers who particularly enjoyed or disliked only a portion of the franchise. ANOVA was selected as the statistical test because it can handle more than two sample means and the ratings data can be reduced to the sample mean as the task is to compare the general assessment of each movie in a given franchise which is given by the mean rating of each movie. 

For the “Star Wars” franchise, the p-value of the ANOVA was 2.399e-38. For the “Matrix” franchise, the p-value of the ANOVA was 1.296e-38. For the “Indiana Jones” franchise, the p-value of the ANOVA was 5.204e-12. For the “Jurassic Park” franchise, the p-value of the ANOVA was 3.542e-10. For the “Toy Story” franchise, the p-value of the ANOVA was 0.00052. For the “Batman” franchise, the p-value of the ANOVA was 1.641e-18. These p-values are less than the alpha cutoff of 0.005. So, it can be concluded that there is a significant difference in the mean ratings of the movies within these franchises and we can reject the null hypothesis that all of the movies within each franchise have a similar or the same mean rating. Therefore, we can also conclude that inconsistency does exist in the quality of the movies within each franchise according to the viewers.

For the “Harry Potter” franchise, the p-value of the ANOVA was 0.23. For the “Pirates of the Caribbean” franchise, the p-value of the  ANOVA was 0.032. The p-values are greater than the alpha cutoff of 0.005. So, it cannot be concluded that there is a significant difference in the mean ratings of the movies within these franchises and we fail to reject the null hypothesis that all of the movies have a similar or the same mean rating. Therefore, we also cannot conclude that inconsistency does exist in the quality of the movies within each franchise according to the viewers.

**Extra Credit:**
“The Fast and the Furious (2001)” is arguably one of the most well known high-speed car movies in recent cinema. The question is: Is there a difference in ratings between viewers who reported liking to drive fast and viewers who reported not liking to drive fast? For this question, ratings for “The Fast and the Furious (2001)” and ratings on the statement “I enjoy driving fast” were extracted from the original dataframe and combined into a new dataframe where NaN values were removed row-wise. This ensures that the data looked at only contains viewers who rated the movie and reported their enjoyment level of driving fast. Ratings on enjoyment of driving fast range from 1-5 so the rating 3 was taken as the splitting point where viewers who rated their enjoyment of driving fast as less than a 3 do not like driving fast and viewers who rated their enjoyment of driving fast as greater than 3 do like driving fast. Using the data split at 3, a Mann-Whitney U test was conducted with the viewers who do like driving fast and the ones who do not. Mann-Whitney U test was selected as it will compare the sample median ratings of the two groups split on enjoying driving fast which is the appropriate parameter to use since ratings data is qualitative. The resulting p-value of the Mann-Whitney U test was 0.15 which is greater than the alpha cutoff of 0.005. So, we cannot conclude that there is a significant difference in the median ratings of “The Fast and the Furious (2001)” between viewers who reported to like versus dislike driving fast. We also then fail to reject the null hypothesis that the mean ratings between the two groups are similar or the same.

![alt_text]()


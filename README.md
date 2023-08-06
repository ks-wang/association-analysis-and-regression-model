# Association Analysis and Regression Model
## with Sleep Efficiency Dataset

### Introduction
Sleep is one of the crucial factors for maintaining health and well-being. By measuring sleep efficiency, we can understand how various components of a person’s lifestyle are affected or affect that person’s sleep. Approximately one-third of adults in the United States reported they are not receiving enough sleep or rest each night, according to the National Heart, Lung, and Blood Institute. 

While choosing datasets, our team found that each of us has very different sleep schedules and was very interested in how and why we could have such different sleeping routines when all of our lifestyles and habits are similar. Thus, we have found the sleep efficiency topic to be the most interesting one of all. Not only is sleep efficiency associated with all of us, but it is also the puppet master behind our decisions and choices.  Moreover, researchers can refer to this analysis to study further research leading to mental and physical illness, health, and treatments for sleep-related disorders. Due to these reasons, we have decided to use sleep efficiency data for our research purpose.

Sleep efficiency data set is a study conducted by the University of Oxfordshire. It is conducted using self-reported surveys, actigraphy, and polysomnography. The dataset contains 15 columns, and we divided them into 3 main categories: 

1) The first part is AGE and GENDER, which are related to each test subject.

2) The second part is sleep-related variables. Sleep duration is the total amount of time the test subject slept (in hours), which is the difference between wake-up time and bedtime.  Sleep efficiency is the proportion of time in bed spent asleep. Lastly, the number of awakenings, light sleep percentage, deep sleep percentage, and REM sleep percentage represent the 4 sequences of the sleep cycle. While the awakening variable indicates the amount of time a candidate wakes up during sleep, REM Sleep Percentage, Deep Sleep Percentage, and Light Sleep Percentage variables indicate the amount of time an individual spends in each stage of sleep. If test subjects have an ideal night's sleep, they would repeat this cycle four to five times.

3) The other variables that are taken into the research are test subjects’ lifestyle patterns and habits, such as Caffeine consumption, Alcohol consumption, Smoking status, and Exercise frequency, to identify whether any potential areas are encouraging or disturbing sleep quality. Caffeine consumption and Alcohol consumption are recorded 24 hours before sleep to see the effectiveness of sleep efficiency and Smoking Status and Exercise Frequency for the long-term effect that it can have on sleep. 

Among these 15 variables, Gender and Smoking Status are the only two categorizable values that are later turned into binary values in the data cleaning stage for better analysis.

We have 452 samples in our dataset. 

### Data Cleaning
Before we start with our analysis of our research, we must do data cleaning. Data cleaning is an essential part of any research. It helps the researchers understand the data more. We started by looking at our dataset and finding any nulls and N/As in the dataset. We found missing data in the Awakening column in 20 missing samples, Caffeine consumption in 25 samples, Alcohol consumption in 14 samples, and Exercise frequency in 6 samples. Since we only have 452 samples, we concluded that dropping missing data would not be the best option to result in a reliable analysis. Instead, we cleaned our missing null data by finding the median for the quantitative variables and imputing those null values with our median values.

For the column with categorical values, for instance, the smoking status column, we converted the Yes and No values to 1 and 0 (i.e., yes for smokers and 0 for non-smokers). Lastly, as using different age brackets for survey data can also offer a deeper analysis of the research and help us understand how each age group’s lifestyle habits could affect sleep efficiency, we created an age group column and split ages into each relevant age group by using FOR Loop and IF Else command. For example, the age between 20 to 29 goes into the 20s age bucket. By doing so, we have created 6 different age buckets based on the youngest sample age of 9 and the oldest sample age of 69 (i.e., Under 19, 20s, 30s, 40s, 50s, and 60s).

### Association Analysis

Following the thorough data cleaning process, our team made the decision to designate sleep efficiency as our dependent variable.  To check whether there is any relationship between the test subjects’ Gender and Age and Sleep efficiency, we drew a scatter plot. However, the points appear randomly scattered, and we were not able to find any meaningful patterns or associations between our dependent variable and the test subjects’ Gender and Age. 

<img width="281" alt="Picture1" src="https://github.com/kaishihwang/Sleep-Efficiency-Dataset/assets/131721638/4a888739-bf87-478e-ada3-89fc9442acb5">

Next, we observed the QQ plots for quantitative variables to determine if our dataset follows a normal distribution. Except for the QQ plot of Sleep Efficiency, all variables’ QQ plots are not a good match, and many data points are away from the diagonal line. Therefore we concluded that the median value provides a valuable summary of the typical value in further analysis. 

![Picture12](https://github.com/kaishihwang/Sleep-Efficiency-Dataset/assets/131721638/884299b1-8904-4185-9a63-f3bc6ab81c9d)

We conducted a correlation matrix analysis, presenting the results in both visualized plot and table format for a clear overview. Through this exercise, we discovered a crucial insight. A zero standard deviation for a variable, indicating that all the variable's values are identical, can cause errors in the correlation matrix. Thus, it becomes necessary to identify and remove any columns with zero standard deviation to compute the correlation successfully. In our correlation matrix, we identified the three variables that exhibited the strongest positive correlations with sleep efficiency.

![Picture13](https://github.com/kaishihwang/Sleep-Efficiency-Dataset/assets/131721638/3aa3e37f-9ea8-4060-92f6-ee2e96248437)

Firstly, the plot between sleep efficiency and Deep.sleep.percentage indicates a non-linear relationship. Given this, we employed Spearman’s rank correlation for our analysis. With a p-value less than 0.05, we can assert that the association between sleep efficiency and Deep.sleep.percentage is statistically significant. The confidence interval range between 0 and 0.007, not including 0.05, which demonstrates the test is conclusive. Next, we examined Exercise.frequency. The plot exhibited a non-linear relationship, so we used Spearman’s rank correlation to proceed with the test. We found the association is statistically significant with a p-value less than 0.05. The confidence interval range between 0 and 0.007, not including 0.05, which demonstrates the test is conclusive. Lastly, we examined Age. The distribution of data points in the plot was intriguing, possibly warranting the use of Pearson’s correlation. However, if we consider the QQ plots we previously presented, some outliers become evident. Given this, we decided to use Spearman’s rank correlation. The p-value of 0.1 indicates that the association is not statistically significant. Moreover, the true p-value for Spearman's rank correlation is expected to fall between 0.075 and 0.13, further confirming our test is conclusive.	

![Picture14](https://github.com/kaishihwang/Sleep-Efficiency-Dataset/assets/131721638/a6153163-9b6f-4b1b-95c8-f7061b0b826f)

Since we could not identify any relationship between test subjects’ physical characteristics (i.e., Gender and Age),  our team separated those characteristics and further analyzed the association between test subjects’ gender and various sleep quality-related variables. Among 4 sleep-related qualities, REM sleep Percentage shows the most statistically significant and conclusive result. The result shows that the p-values from both Mean and Median tests are less than 0.05, and 0.05 is not inside the range. Moreover, another exciting association analysis our group conducted is between an age group and sleep efficiency.  By doing so, the Side-by-side boxplots clearly show that the distribution of our dependent value Y varies between levels of age group. Also, in our statistical analysis, the p-value from the ANOVA test is 0, and 0.05 is not inside the range; we concluded that the test is statistically significant and conclusive. 

![Picture15](https://github.com/kaishihwang/Sleep-Efficiency-Dataset/assets/131721638/50fcfc4f-4915-41ae-ab44-1fac8ac0736e)

In contrast, we analyzed the three variables that demonstrated the strongest negative correlations with sleep efficiency. For Light.sleep.percentage, the plot indicated a non-linear relationship. Utilizing Spearman’s correlation, we discovered a p-value of 0, implying a statistically significant association. The confidence interval ranges between 0 and 0.007, not including 0.05, which shows the test is conclusive. Next, we examined the association between Sleep efficiency and Awakening. We chose Spearman's rank correlation, determining the association to be statistically significant with a p-value less than 0.05. The confidence interval range is not including 0.05, which indicates the test is conclusive. Lastly, we analyzed the association between Sleep efficiency and Alcohol.consumption. We used Spearman's rank correlation to measure the association, finding it statistically significant with a p-value falling under 0.05. This result, in combination with a confidence interval that does not include 0.05, establishes the conclusiveness of our test.

![Picture16](https://github.com/kaishihwang/Sleep-Efficiency-Dataset/assets/131721638/ac39a6c0-7454-4146-a8cd-d8a0c320d6ed)

We also applied logarithm transformations to the above variables to attempt to linearize the relationships. However, the plots still showed non-linear relationships. We concluded that a logarithm transformation does not guarantee linearity. Other factors, such as additional influencing variables or heteroscedasticity, may contribute to the non-linear and non-monotonic appearance. Exploring other transformations (such as converting sleep efficiency into different group levels) might be necessary, or considering other modeling techniques to capture more complex relationships.

### Regression Model
Since Deep Sleep Percentage and Light Sleep Percentage were our strongest variables, we further compared these variables with our dependent variable, Sleep Efficiency, in the linear regression model to see if they were significant. 

![Picture17](https://github.com/kaishihwang/Sleep-Efficiency-Dataset/assets/131721638/9366d4fc-9383-4f2d-a2b1-cca1b31507ec)

Observing the figure above, in the linear regression between sleep efficiency and deep sleep percentage, we can see that the coefficient of the regression is at 0.0068, which suggests the increase in sleep efficiency when a unit of deep sleep percentage increases. The intercept starts at 0.43, which is the starting point of the regression or the value of sleep efficiency when the deep sleep percentage is at 0. Furthermore, we see the R-squared at 0.6191, suggesting that the correlation between sleep efficiency and deep sleep percentage is moderately strong, and the regression approximates the actual data well. At the bottom, we can observe the p-value to be less than 2.2e-16, which is less than a 0.05 significance level, suggesting that the regression between sleep efficiency and deep sleep percentage is statistically significant. At first glance, the scatterplot comes out to be unnatural. However, if we observe carefully, we see that although there is no linearity in the plot, there is a correlation in variables as when deep sleep percentage increases, we see the values in sleep efficiency also increase. There is a jump at 0.7 which would be the plot’s weakness, but our team believes this is because of the small sample size in the data especially for the middle values of the variables.

![Picture18](https://github.com/kaishihwang/Sleep-Efficiency-Dataset/assets/131721638/1dcccf3b-3490-4753-913b-c2ef4a488a86)

In contrast to deep sleep percentage, we can observe in the regression table that the relationship between light sleep percentage and sleep efficiency is negative. The coefficient of the regression is at -0.0072345, suggesting that with every one-unit increase in light sleep percentage, the sleep efficiency decreases at that coefficient. However, the intercept starts at positive, at 0.9666, when the sleep percentage is at 0. The R squared is at 0.6704, suggesting a moderately strong relationship between the variables. Finally, the p-value is at the same value as the deep sleep percentage, which is less than 2.2e-16 suggesting the statistical significance between the two variables, light sleep percentage and sleep efficiency. As we move on to observe the plot, we notice a similar pattern with the deep sleep percentage plot where there are missing values in the middle, with the big jump at 0.7%. However, we can still conclude that although there might be no linearity, there is still a correlation between the variables, as when light sleep percentage increases, we can observe a decrease in the values of sleep efficiency. To make both plots more viable, we would need a bigger sample size in the testing data. 

### Other Techniques
### Multiple Linear Regression 

![Picture19](https://github.com/kaishihwang/Sleep-Efficiency-Dataset/assets/131721638/291a3351-3234-4d36-8cec-55257b5c778f)

Next, we did multiple linear regression with all the variables in the data to further analyze which variables were significant to our dependent variable. We excluded the light sleep percentage variable this time as we deduced that it depended heavily on deep sleep percentage when we performed linear regression. In the regression table, we can observe that the variables, Age, REM Sleep Percentage, Deep Sleep Percentage, Awakenings, Alcohol Consumption, Smoking Status, and Exercise Frequency, were all statistically significant due to all of their p-values being less than 0.05 significant level. With RSE at 0.06 and R squared at 0.8003, we can conclude that these variables were all affecting our dependent variable, sleep efficiency. Although we initially believed that sleep duration and caffeine consumption were the deciding variables, it was shocking for our group to analyze that they were insignificant in determining sleep efficiency. Decision tree analysis
We decided to choose decision tree analysis next; our purpose is to identify the most important predictors of sleep quality and how they interact with each other to develop a predictive model that can help better understand better and improve sleep quality in the future. By using a decision tree, we can visualize the relationships between different variables and how they contribute to predicting sleep quality and identify the most important factors that influence sleep health.
In this analysis, we used the tree() function in R to build a classification tree that predicts sleep quality based on a set of predictor variables. The predictor variables included in the analysis were Age, Sleep.duration, Awakenings, Caffeine.consumption, Alcohol.consumption, Smoking.status, and Exercise.frequency. Before we proceed with the analysis, we transform quantitative data sleep.quality into 4 categorical data: “Excellent: 90-100, Good: 80-89, Fair: 60-79, Poor: Below 60.

### Decision tree analysis
We decided to choose decision tree analysis next; our purpose is to identify the most important predictors of sleep quality and how they interact with each other to develop a predictive model that can help better understand better and improve sleep quality in the future. By using a decision tree, we can visualize the relationships between different variables and how they contribute to predicting sleep quality and identify the most important factors that influence sleep health.

In this analysis, we used the tree() function in R to build a classification tree that predicts sleep quality based on a set of predictor variables. The predictor variables included in the analysis were Age, Sleep.duration, Awakenings, Caffeine.consumption, Alcohol.consumption, Smoking.status, and Exercise.frequency. Before we proceed with the analysis, we transform quantitative data on sleep.quality into 4 categorical data: “Excellent: 90-100, Good: 80-89, Fair: 60-79, Poor: Below 60.

For the outcome, the most critical predictor variable for predicting sleep quality is Awakenings. This variable is used as the first split in the tree, with a cutoff value of 1.5. Sleepers with 1.5 or fewer awakenings per night are likely to have better sleep quality, while sleepers with more than 1.5 awakenings per night are likely to have poorer sleep quality.

Age is the following most crucial predictor variable among sleepers, with 1.5 or fewer awakenings per night. Sleepers who are 41.5 years old and below tend to have good sleep. Otherwise, sleepers who consume less than 0.5 alcohol will likely have excellent sleep. 

Among patients with more than 1.5 awakenings per night, the following most crucial predictor variable is alcohol consumption.  Sleepers who consume less than 0.5 alcohol tend to have a fair sleep quality. Otherwise, if they are younger than 42.5 years old and sleep less than 7.75 hours are likely to have poor sleep.

The other predictor variables (Caffeine.consumption, Alcohol.consumption, Smoking.status.binary, and Exercise.frequency) do not contribute significantly to predicting sleep quality in this model.

![Picture20](https://github.com/kaishihwang/Sleep-Efficiency-Dataset/assets/131721638/8b1d1c2d-d3d8-4df1-b6fd-c59f04173b5c)

## Authors
Kai Shih Wang 
Kaung Mon Htet
Yoon Young Kim
Khine Hsu Wai
Thy Bui

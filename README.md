# Examining the Factors that Influence Pathrise Fellows Getting a Job

For a data science challenge, I looked at the factors that influence whether or not a Pathrise fellow will land a job. For those unfamiliar with Pathrise, they are a career-accelerator startup aimed at helping its fellows land a career through mentorship and career-related resources. More information on them can be found on their website [here](https://www.pathrise.com/).

## My Goals
I wanted to analyze the factors that influenced fellows landing a job. More specifically, I was to **predict whether or not a fellow will be placed** and **how long it takes for a fellow to be placed**. Then, I'd make recommendations to Pathrise based on my analysis. 

My goal wasn't to build an effective model, but to **understand and intepret the features that impact fellow placement and make recommendations accordingly**. 

## Getting the Data
The data was given to me as a challenge. It contains various data on fellows who have joined from 2018 till now, including their Pathrise track, number of years of professional experience, education experience, and whether or not they placed at a company. 

## My Thought Process in Solving this Problem
I followed 5 steps:
1) Deal with missing data. 

For most of the data, I imputed the missing data as a new level if it was a categorical variable, or imputed the missing data as the median if it was a quantitative variable. I did this because getting rid of these variables or missing data would get rid of a lot of my observations.

2) Analyze the response variables. 

There were two variables to look at: fellow placement and fellow placement time. For fellow placement, I examined the distribution of the different predictor variables between placed and non-placed fellows, and found that there were similar distributions amongst the two. For fellow placement time, I found that it was a non-normal distribution and thus had to log-transform it.

3) Explore the predictor variables.

Categorical variables made up a majority of my dataset. I found that most fellows in this dataset, regardless of placement, were in the SWE track, completed either a Bachelor's Degree of Master's Degree, has less than a year to two years of experience, are US Citizens, and have been looking for a job for less than a month to two months.

There weren't a lot of quantitative variables; the data only gave me data on the number of applications and interviews a fellow had. So, I constructed new variables, such as the years the fellow was in their Pathrise cohort, and interview turnout i.e., the number of interviews divided by the number of applications. Most fellows place at a company after around 3.5 months.

4) Model the data.

I started off simple, and used a logistic and linear regression to predict whether a fellow will place and how long it will take for them to place, respectively. I realized that these models overfitted and that there was a lot of variance in my data. So, I used XGBoost for both problem sets, as boosting algorithms can reduce variance and bias, effectively. The XGBoost library can also let me know which features are important, which is a powerful tool for interpretative problems.

5) Make some recommendations based on these insights and modelling.

I'll explain this in more detail in the next section.

## Results and Recommendations

My main recommendation for Pathrise is this: **emphasize to fellows early on that it's not the amount of applications sent out, but the quality and where these applications are sent.** 

Making this clear is crucial so that fellows don't wear themselves out in sending out applications. Once fellows send out an amount of applications above the median, which is 20, then more of them withdraw from the program. In fact, almost 44% of fellows who haven't placed have withdrawn from the trial or the entire program after sending out more than the median number of applications. 

## Possible Future Projects
**Looking at ways to make fellows stay in the program**.

According to the Pathrise website, the average number of months a fellow takes to place at a company is 3.5 months. As there really is no difference between placed and non-placed fellows i.e., the distributions of the predictor variables are similar, then this, to me, means that fellows place at a company as long as they stay in the program. However, most fellows leave their cohort after around 2 months. Why is that?

If given more data e.g., feedback on why these fellows leave, I'd love to analyze the features that impact fellows leaving Pathrise and see how to prevent this. 


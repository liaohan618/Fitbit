# Fitbit Fitness Data Analysis & Sleep Score Modeling

## Description
Fitbit is an electronic company that make smartwatches that could be used as fitness tracker. In this project, I analyzed my personal fitness data that were tracked by my Fitbit Inspire 3 smartwatch from late June to early December. I aim to find factors that affect my sleeping and calories burning. 

## Dataset
I exported data from my Fitbit smartwatch. The original data were composed of multiple files, each file represent a measurement. Some of the factors are measured once a day (ie. sleep_score and deep_sleep_min), other factors that are related to heart beat, calories, etc. are measured in very short time interval. Thus, for factors need to be cumulated (ie. calories), I summed it up for each day. And for factors like resting_heart_rate, I took the average for each day. Thus I obtained a dataframe that each row represent the data for each date. Lastly, I changed the column names to be easier read and converted the data types, so the final dataframe "fitbit_df" will be used for this project.

## Problem Statement
1. Which are the factors that affect sleep score the most?
2. Which are the factors that affect calories burned the most?
3. How is sleep score calculated?

## Findings
1. sleep_score
   - Factors that are most important to sleep_score are stress_score, deep_sleep_min, and date
     - By using linear regression model with specified recipe, I am able to obtain a model with rsq=0.79, rmse=2.62
   - However, how stress_score is calculated is also remain unknown, so I created another model without stress_score
     - By using linear regression model with specified recipe, I am able to obtain a model with rsq=0.814, rmse=2.36

2. calories
   - Calories is mostly associated with AZM_minutes (Active Zone Minutes)
     - Counterintuitively, it does not have strong relationships with factors that are related to sleeping
   - After exploratory data analysis, I realized that I did not input my weight and height, which is curcial in determining calories burning
   - I also do not have number of steps, despite it could be related to AZM_minutes
   - Thus, I decide not to model calories for now

3. Date plays a crucial role in the modeling process. For instance, In July, August, and Spetember, there is a significant change in my sleep score trends that I have to consider date while predicting. And these 3 months happen to be Summer break, which makes sense that my rountine was different from regular school days.
   
## Improvement
- There are many other counterintuitive findings such as sleeping and calories burned are not quite related to heart rate or oxygen, etc. I doubt this is due to the reason that the smartwatch is not tracking accurately sometimes, and also I am wearing it for half a year, after removing missing values, there were only 135 rows remain.
- There are some important factors that were not in my dataframe. For example, number of steps, starting and ending time of sleep, duration of sleep, etc.
- There are some other factors I could consider in the future. For example, if I drink coffee or tea in the afternoon (binary), if I workout at night (binary), if I do meditation before bed (binary), etc.

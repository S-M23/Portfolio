# Linear Regression on Gym Dataset

Access to Project here: [Linear Regression on Gym Dataset](https://s-m23.github.io/Portfolio/)

## Research Question – What impact does workout session duration for members of the gym have on their body fat percentage, and how can a regression model be used as supporting evidence to encourage members of the public to prioritise their activity levels?

### Executive Summary
A simple linear regression model was run on the gym_members_exercise-tracking.csv dataset (sourced from Kaggle.com) to assess how weekly workout session duration (in hours) affects the body fat percentage of members. Body fat % was the dependent variable and weekly gym duration was the independent variable. 

The results show that workout duration does have an impact on body fat %, as does water intake. Based on this linear regression analysis, increasing weekly workout duration by one hour is associated with a 1.65% decrease in body fat percentage. Therefore, it can be recommended to incorporate an additional hour of exercise into weekly routines to help reduce body fat. 

The analysis also suggests drinking more water can aid in reducing body fat, so an extra litre a day alongside increased workout duration may have an even larger impact.

The model can be rerun on real data and insights can be used to produce factual statistics around the small changes people can make to better get in shape. This will provide benefit to communities who require more of a focus on preventative care, saving healthcare organisations time and money, boosting gym membership uptake all whilst improving quality of life for individuals.

### Project Background
The gym members dataset presents 973 rows of data, each one detailing information about different members of the gym. The data collected around these members is as follows:

Age

Gender

Weight (kg)

Height (m)

Max_BPM

Resting_BPM

Session_Duration (hours)

Calories_Burned  

Workout_Type

Fat_Percentage

Water_Intake (liters)

Workout_Frequency (days/week)

Experience_Level

BMI

The insights taken from the results of the analysis may be useful in informing members of the public how impactful gym sessions can be on body fat %. Although this dataset is an open one and accessible at Kaggle.com (Gym Members Exercise Dataset, no date), it may be a great way to promote active lifestyle changes in members of the community. There is a potential opportunity to share statistics that may encourage people to join their local gym for their general health.

### Process
The first step is to download the dataset and do some initial exploratory data analysis (EDA) on it. This includes assessing the data quality and visualising pairs of variables that could show potential correlation.

![Fig 1 and 2](https://github.com/user-attachments/assets/9c09d6c1-a9be-4608-b59e-2b8622ab648f)

### Data Quality
It’s useful to open the file in Excel and use the autofilter function and conditional formatting on each column to find any null values, incorrect formatting, and potential invalid values. A general sense check gives an idea of what the data should look like and, as a rule of thumb, these can be amended individually using different Excel features. For example, the ‘Find and Replace’ feature can identify nulls in a specified column and can be replaced with ‘0’ if that is what’s required. 

Python is another great tool to use for data quality and EDA. No nulls or duplicates rows were identified in this dataset however if there were, they would be either replaced or removed.

Correlation tables and scatter plot matrices visualise correlation between all numerical variables. A plot is easier to look at than the correlation in a table. There is high collinearity (>0.8) between session duration (hours) and calories burned. This could cause issues such as unstable coefficients where both show high sensitivity to small changes in data. It is best to remove calories burned from the dataset before proceeding, as the ‘calories burned’ column is not being used in this regression. An alternative would be to use Principal Component Analysis (PCA) to transform the correlated predictors into a set of unrelated components. 




![Fig4](https://github.com/user-attachments/assets/141574d6-f0d0-4dbd-b55f-b80e18171360)
The remaining columns after dropping those that are highly correlated:

Box plots show distribution and identify outliers.

![Fig5](https://github.com/user-attachments/assets/c433f386-79c8-4754-b1a4-7b01627ddbda)


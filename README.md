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

![Gym correlation table](https://github.com/user-attachments/assets/4eb55cdd-8d09-44a3-953c-e2f4c58a2784)

![Fig3](https://github.com/user-attachments/assets/9312e7b5-3e51-4ea7-8183-c288ccdf551c)

The remaining columns after dropping those that are highly correlated:

![columnsafterdropped](https://github.com/user-attachments/assets/19a09a42-75e3-42e2-aac2-38428aaaf598)

![Fig4](https://github.com/user-attachments/assets/c1dcbe04-9b88-4a5c-87d4-4aa8b16d5fd5)

Box plots show distribution and identify outliers.

![Fig5](https://github.com/user-attachments/assets/cbc88f2a-6aaf-40d5-aeb0-0c8c1d20dec2)

Histograms show the spread of the data.

![Fig 6 and 7](https://github.com/user-attachments/assets/3b8ff5b1-e046-40df-aebe-3a52348730c4)

Correlation heatmap matrices show differences in correlation between different variables. 

![Fig8](https://github.com/user-attachments/assets/e0f26861-3ad6-44f7-8c3b-73b62fa23c66)

### Data Transformation
I carried out some feature engineering on my dataset; I created an ‘Average_Weekly_Workout_Duration (hours)’ field by multiplying ‘Session_Duration (hours)’ by ‘Workout_Frequency (days/week)’ in my Excel file. I also created an ‘Average_Weekly_Calories_Burned’ by multiplying the ‘Calories_Burned’ by ‘Workout_Frequency (days/week)’.

It is important to note that I have assumed that gym members spend the same amount of time at the gym AND do the same workouts on each of their gym sessions, therefore burning a similar amount of calories.

### Data Visualisation
There are many tools available to me to visualise the data. Excel is an obvious one where graphs can be created using different variables. Python is also a great tool to use for visualisation and allows me to keep data quality, EDA, visualisations and analysis all in one notebook. For the purposes of this project, however, AI tool Claude was initially used to create a simple dashboard as it mitigates the need to code and gives suggestions based on the dataset. There are limitations of using this tool, for example the data was interpreted to be reported over time despite no date field being available. Not many of the charts produced provided valuable insights. Therefore, Tableau was used as a more reliable tool to produce a summary of some of the fields available.

#### Visuals produced by ClaudeAI:
![Fig9](https://github.com/user-attachments/assets/7d4942ad-87df-468b-a2bd-229232872f22)

As the data is not real, there aren’t many safety or privacy concerns when using emerging AI tools to interpret the data. In real life scenarios, handling sensitive data is a challenge and compliance with data protection regulations is crucial, meaning that tools such as Claude AI may not be approved of to produce quick visuals. 
New tools in general require much staff training, and, although this uses valuable time, is essential in making the most of the investment. Tableau is used widely across my organisation, however, even after 8 years of this tool being available, staff have struggled to use it to its full potential. Although newer resources may be available, an evaluation of whether they are a right fit for the company and its employees is important to help find a balance between staying up to date with data science releases and realistic application in the workplace. 

![Fig10](https://github.com/user-attachments/assets/a1c210d2-d4d6-4ee5-8ed5-84c6f4c82703)

### Data Analysis
A linear regression model examines the relationship between weekly workout session duration and body fat %.
Python is the tool being used and the steps followed are:

1.	Importing libraries and loading my dataset. Includes data quality and EDA. Sklearn Linear Regression model used for analysis.
   
2.	Define the independent variable (weekly workout duration) and dependent variable (body fat %).

3.	Split data into train and test set – the dataset was split into 70% training data and 30% test i.e. 681 rows train set and 292 test set. As this is a smaller dataset, a 70/30 split has been used over 80/20.
   
The target and input variables are separated in both test and train sets so the model can learn the relationship between inputs and targets without any bias:

X_train = df_train.drop('Fat_Percentage', axis=1)

X_test = df_test.drop('Fat_Percentage', axis=1)

y_train = df_train['Fat_Percentage']

y_test = df_test['Fat_Percentage']

![Fig11](https://github.com/user-attachments/assets/598db1c3-06fd-43fe-86a1-05f5e143337a)

4.	Create linear regression model and train with training data – after training the linear regression model and evaluating performance of trained model on the test data, the R-squared value produced is 0.589 (to 3 significant figures). 
Intercept and coefficients of the model:
Intercept – 54.63
Coefficients –

0	Age	0.014502

1	Height (m)	-5.453729

2	Max_BPM	-0.003598

3	Avg_BPM	-0.009033

4	Resting_BPM	-0.006301

5	Water_Intake (liters)	-3.598221

6	BMI	-0.073089

7	Weekly_Workout_Duration (hours)	-1.645920

Body Fat % = 
        54.63 + (0.014502 * Age) + (-5.453729 * Height (m)) + (-0.003598 * Max_BPM) +  (-0.009033 * Avg_BPM) + (-0.006301 * Resting_BPM) + (-3.598221 * Water_Intake (liters)) + (-0.073089 * BMI) + (-1.645920 * Weekly_Workout_Duration (hours))


The coefficient of weekly workout duration suggests that for each additional hour of workout per week, the body fat percentage decreases by 1.65%.

The water intake coefficient suggests that for each additional litre of water intake, body fat percentage decreases by 3.60%. Research from PubMed Central around water intake suggests that ‘Drinking water can stimulate your body to break down fat without raising your blood sugar or insulin, which may also support weight loss.’ However, this may be ‘only in people of average weight and body mass index (BMI)’ (How Drinking More Water Can Help You Lose Weight, 2017). An additional analysis could be carried out to discover potential relationships between BMI, water intake and body fat % in our dataset. 

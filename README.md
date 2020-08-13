# Salary_Prediction
## Objective
To examine a set of job postings with salaries and then predict salaries for a new set of job postings.

## Dataset:

The dataset contains three CSV data files:
- train_features.csv: Each row represents metadata for an individual job posting.The “jobId” column represents a unique identifier for the job posting. The remaining columns describe features of the job posting.
-	train_salaries.csv: Each row associates a “jobId” with a “salary”.
-	test_features.csv: Similar to train_features.csv, each row represents metadata for an individual job posting.
The first row of each file contains headers for the columns. 

## The task
To build a model to predict the salaries for the job postings contained in test_features.csv.

## Exploratory Data Analysis:
In the EDA section in the notebook analysis are performed to find relationships between each variable and the target variable.

## Examining outliers:
The salary column is examined for outliers by analyzing the IQR of the variable. The lower bound & upper bound were found to be 8.5 & 222.5 respectively. On analyzing the rows with salary less than 8.5 , it was found to have zero. These instances are either corrupt or incorrect information and hence can be removed. On analyzing the instances with salary > 222.5 it was found that most job types were either C-level executive roles(CFO, CTO etc.) or junior roles working for high paying industries such as oil, finance. Therefore, these instances are found to be legitimate and can be used for predicting the target variable.

The plots and other inferences are presented in the salary_prediction_EDA.ipynb file.

## Feature Engineering:
The categorical variables ('companyId', 'jobType', 'degree', 'major', 'industry') are encoded using label encoding. This enables the model to understand the data better and produce better predictions.

The mean, min, max, std, median, mean of all the categorical columns are grouped and created as different variables as these can have some relationship with the target variable salary. The salary of a job can be based on these statistics, hence these variables are engineered for better predictions.

## Predictive Model:
To predict the salary variable three regression models (Linear Regression, RandomForestRegressor, GradientBoostingRegressor) are tested to find the best one using the metric ‘MSE’. The best model was found to be GradientBoostingRegressor with an MSE of 313.2 . Therefore, the GradientBoostingRegressor model is used for the final prediction and the feature importance of the variables are plotted to have better understanding on the prediction. 

## Note:
- The feature engineered variable group_mean has the highest importance in predicting the salary
- The yearsExperience & the milesfromMetropolis are the other two important features in predicting the salary


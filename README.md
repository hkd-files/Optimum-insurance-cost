→ We all know that Health care is very important domain in the market. It is directly linked with the life of the individual; hence we have to be always be proactive in this particular domain. Money plays a major role in this domain, because sometime treatment covered under the insurance then it will become a pretty tough financial situation for that individual. The companies in the medical insurance also want to reduce becomes super costly and if any individual is not their risk by optimizing the insurance cost, because we all know a healthy body is in the hand of the individual only. If individual eat healthy and do proper exercise the chance of getting ill is drastically reduced.

→ The objective of this exercise is to build a model, using data that provide the optimum insurance cost for an individual. we have to use the health and habit related parameters for the estimated cost of insurance.

→ This case study will be very useful for company to identify most common health condition and by using that company can promote their health plan for that particular health disease/problem.

### Skills and Tools used
→ Cluster Analysis · Exploratory Data Analysis · Hypothesis Testing · Machine Learning · Data Visualization

### Data description
→There are 25000 rows and 24 columns present in dataset → There are 16 numeric and 8 object data types present in the data → I have removed variable ‘applicant_id’ as it does not provide any significant information & just a continuous number → No duplicare value present in dataset and Missing value does exist in dataset.

### Univariate and Bivariate analysis
![image](https://github.com/hkd-files/Optimum-insurance-cost/assets/132456697/4e1ced3e-6e05-43f8-84fc-58b517ce8691)
![image](https://github.com/hkd-files/Optimum-insurance-cost/assets/132456697/8d6f02ea-ff27-4bda-933a-d662828688d4)

### Steps that followed in data cleaning
→Outliers have been treated by using IQR method → Missing values have been replaced with median and entire column ‘Year_last_admitted’ has been dropped because 47% values were missing → Anova test has been performed to know significance of categorical variables and only one of the variable ‘covered_by_any_other_company_Y’ found significant therefore all other variables have been removed → At last i only have 15 variables available whereas we had 24 variables so i was able to do dimensionality reduction. 

### Models that i have built
As we know that we are trying to build a model which can provide optimum insurance cost and here target variable insurance cost is a regression problem therefore we have built different regression models and chose best model after comparing all model performances.
1. Linear Regression from stats model 2. Linear Regression from Sklearn 3. Decision Tree Regressor 4. Random Forest Regressor 5. Ridge Regressor 6. Lasso Regressor 7. XGBOOST (EXTREME GRADIENT BOOSTING) REGRESSOR

### model’s Performance comparison table
![image](https://github.com/hkd-files/Optimum-insurance-cost/assets/132456697/325872f0-0d57-45ac-9870-7fadecaeab41)

### Best fit model
Based on Comparison table we can see that all models performance is quite good except (XGB Due to overfitting) but if we have to pick one model out of all then it will be Decision Tree Regressor because of it’s lowest MAPE and high R Squared.
###### Key takeaways from best DTR model
1. R-squared of 95 indicate that 95% of variance in dependent variable(insurance_Cost) has been explained by independent variables collectively.
2. RMSE score of 0.22 indicate avg. difference between predicted and actual values as it’s an error so we expect it to be lowest.
3. MAPE score of 10 indicate that DTR model predictions are, on average, off by 10% from the Actual values.

### Feature Importance From DTR Model:
![image](https://github.com/hkd-files/Optimum-insurance-cost/assets/132456697/a6b4f864-19a4-4820-9b28-2ebcd1f41708)

### Insights & Recommendations from Analysis
###### Insights
→ From DTR feature importance, 3 variables: 'other_major_decs_history', 'heart_decs_history', 'adventure_sports' have 0 Coefficient that means these variables have no contribution in predicting Insurance Cost therefore these are not important so these can be ignored.

→ Weight is the most important variable as it alone has coefficient of 0.99 that means this variable has 99% contribution in predicting insurance cost and same we observed in Heatmap that this variable was highly correlated with Target variable and our model also proved it.

→ Weight being an important variable sounds logical as we know that overweight has high effect on health it can be reason of many disease and therefore other variables such as BMI, Fat_percentage, Avg glucose level, heart_decs, other_decs all these are related to weight if weight is in control then these variables will also be in control in most of the cases except genetics based disease.

→ As we have seen that Weight is very important variable for predicting insurance cost and there is similar variable present which is ‘Weight change in a year’ but this variable is not so so important for prediction based on feature importance and this might be because change in weight is not specified whether weight has increased or it decreased in last 1 year so this needs to be noted carefully while collecting data whether weight change leading to weight increase or decrease and if this is obtained then this variable might be very helpful to find out individuals recent activities towards his/her health.
###### Recommendations
→ As we have seen that all model performed quite well and Linear regression provided 4 most important variables( ‘regular_checkup_lasy_year’, ‘weight’, ‘weight_change_in_last_one_year’, ‘covered_by_any_other_company_Y’) so these variables need to be checked properly  
→ Out of those 4 variables one variable ‘Weight’ was found very important in EDA where we observed that target variable is highly correlated with this variable. 

→ As we stated that DTR is best model and DTR model does provide Feature importance and in this DTR model  3 variables are really not important as value of those variable is zero so they don’t contribute in prediction at all. 

→ These are 3 non important variable as per DTR model adventure_sports, heart_decs_history, other_major_decs_history and same we observed in our linear equation that these variables were removed as these were non-significant so company don’t need to give more weightage to these variables 

→ There might be few important variables such as past claim history, past claim settlement amount or any other claim related details because these details can provide additional information about an individual’s frequent illness, disease, cause of illness etc.

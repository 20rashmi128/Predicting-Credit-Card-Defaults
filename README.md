# Predicting credit card defaults (Classification):

# Problem Description
This project is aimed at predicting the case of customers default payments in Taiwan. 
From the perspective of risk management, the result of predictive accuracy of the estimated probability of default will be more valuable than the binary result of classification - credible or not credible clients. 

# Attribute Information:

This research employed a binary variable, default payment (Yes = 1, No = 0), as the response variable. This study reviewed the literature and used the following 23 variables as explanatory variables:

1. X1: Amount of the given credit (NT dollar): it includes both the individual consumer credit and his/her family (supplementary) credit.
2. X2: Gender (1 = male; 2 = female).
3. X3: Education (1 = graduate school; 2 = university; 3 = high school; 4 = others).
4. X4: Marital status (1 = married; 2 = single; 3 = others).
5. X5: Age (year).
6. X6 - X11: History of past payment. We tracked the past monthly payment records (from April to September, 2005) as follows: X6 = the repayment status in September, 2005; X7 = the repayment status in August, 2005; . . .;
        X11 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; . . .; 8 = payment delay for eight months; 9 = payment delay for nine months and above.
7. X12-X17: Amount of bill statement (NT dollar). X12 = amount of bill statement in September, 2005; 
        X13 = amount of bill statement in August, 2005; . . .; X17 = amount of bill statement in April, 2005.
8. X18-X23: Amount of previous payment (NT dollar). X18 = amount paid in September, 2005; 
        X19 = amount paid in August, 2005; . . .;X23 = amount paid in April, 2005.

# About Dataset: 
This dataset contains information on default payments, demographic factors, credit data, history of payment, and bill statements of credit card clients in Taiwan from April 2005 to September 2005. 

For better understanding, the columns of dataset can be categorised as below:
1. Demographical features: Age (Numerical), Sex, Marital Status, Education (Categorical)
2. Behavioural features: History of past 6 months paid amounts (Numerical), Past 6 months Bill amounts (Numerical), 
                      Repayment staus for last 6 months (Categorical), & Maximum credit line approved (Numerical).

# Approach taken:
# • EDA: 
After importing relevant python Libraries, dataset file was loaded,
and I gathered basic details about dataset. Then, univariate analysis for each variable, followed by bivariate analysis to explore the relationships between two variables and multi-variate analysis were done using histograms, bar charts, Correlation Matrix etc. Also, used data visualization tools to get better grasp of underlying trends and patterns.
# • Data Pre-processing: 
Extracted potential features for modelling and encoded categorical variables. After feature engineering, did stratified Train-Test splitting and later transformed predictor variables using MinMaxScaler. Using correlation matrix, SelectKBest filter method , RFE and Sequential Forward selection methods, selected important features for modelling. For handling class imbalances, experimented with various under-sampling, over-sampling and combined re-sampling techniques.
# • Model creation & Evaluation: 
Built simpler baseline models and did evaluation using Recall, precision, and F-1 scores. Further, assessed model’s ability to distinguish positive and negative classes using AUC-ROC and KS- statistics. Also, performed Hyper-parameter tuning of Logistic Regression, XGBoost, RandomForest and SVM classifier models. Further, experimented with moving thresholds for best F-1 score and desired Recall of 0.80.

# Conclusions:
 
1. About Customers:

        a. Majority of customers are Females (~60%).
        b. Majority have University level education (~47%), followed by Graduate school level (~35%). Only 16% have High-school level education. 
        c. Majority(~53%) are single, followed by married customers (~46%). 
        d. Most of customers (~72%) are within 21 years to 40 years age group. 
        e. As per the given dataset, only ~22% customers have defaulted on payment next month.
2. Demographics and Defaults:

        a. Chances of Males defaulting on their payments next month is higher than that of Females.
        b. As education level increases (i.e., high school to university to graduate school), default rate decreases.
        c. Basis Marital status, Chances of defaulting is highest for Married customers.
        d. Customers of age between 31 to 40 years are least likely to default, followed by 21 to 30 years group.
3. Financial Behaviours and Defaults:

        a. Average of maximum credit limit approved for Defaulters is less than that of non-defaulters.
        b. Customers with payments pending for more than 1 month, have higher chances of defaulting.
        c. Defaulter's overall pay-down ratio kept on decreasing each successive month
        d. Defaulter's utilization rate increased significantly in latest month of September, while for non-defaulters the utilization rate decreased.
4. BestPerformingModels:

• Considering Recall metric with utmost importance, followed by Precision and F-1 scores, found the following top 3 models:
        1. SVM model built using TomekLinks datasetis the best performing model, with good Recall (0.57), precision (0.48), F-1 score (0.52), AUC-ROC (0.74) and least Brier score (0.14).
        2. Second best performing model is Random Forest classifier built using SMOTE dataset, with good Recall (0.55), precision (0.48), F-1 score (0.51), AUC-ROC (0.76) and Brier score (0.17).
        3. Third best performing model is XGBoost classifier built using SMOTE-TomekLinks combined dataset, with good Recall (0.55), precision (0.47), F-1 score (0.50), AUC-ROC (0.75) and Brier score (0.17)

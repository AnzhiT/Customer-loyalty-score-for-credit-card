# Customer-loyalty-score-for-credit-card

## Executive Summary

This project aims to predict the loyalty score of ELO by user level and explore what kind of features of credit card tend to lead higher loyalty. The train dataset contains 201,917 lines of customer records with their card ID, card feature, first active month and Target. The transaction data have two parts: historical data in the past 6 months and new period data in the near three months. The data contains card id, card holder’s demographic feature like city and state, purchase amount and time, authorized status and the number of installments of purchase.
For interpretation purpose, we first build a simple decision tree to examine how tree nodes divided in different groups with target as the dependent variable and feature 1, feature 2 and feature 3 as three independent variables. The RMSE is 3.88, which is larger than the standard deviation of target.

We aggregate several purchase records by the same card ID. To get more information of variables, we do different feature-- maximum, minimum, mean, sum and standard deviation of several records based on the nature of each variables and aggregate purchase records by those newly created features. In this way, the prediction accuracy of machine learning model has been increased. The dimension reduction method PCA and machine learning method have been applied together or individually to the aggregated dataset and lightGBM get the best prediction result with RMSE at 3.658.

Optimized promotion time is recommended to the merchandise. For ELO, feature 1 and feature 2 and more effective than feature 3 to classify and detect customer loyalty and design of feature 3 need to be improved.


## Key Findings
From the decision tree model, it is clear that feature 1 and feature 2 take a major role to classify customers. Customers in these groups have an average target value higher than overall average: (1) With feature 1 equals to either 1, 2, 3 or 4 as well as feature 2 equals to 1 or 2; (2) With feature 2 equals to 3 as well as feature 1 equals to 2 or 4. Higher target value indicates that these customers are more loyal than average customers.

From GBM model, The relative importance of different variables are determined (Appendix VII). Out of the 180 variables around 20 variables had a high relative importance (greater than 1) and around 118 variables had a non-zero influence on the model (Appendix VIII). Some of the significant variables are purchase date, purchase amount, month lag and purchase month. This shows that the time period of purchase and the amount of purchase are key factors in measuring loyalty.

From LightGBM model, it is found that purchase date and purchase amount are two important variables. After feature engineering, the features related to purchase date occupy 5 out of the top 10 features. And the most important one is the max purchase_date from authorized transactions, followed by the max purchase_date from new transactions. For purchase amount related features, new_purchase_amount max purchase amount from new transactions and the mean of max purchase amount also have high importance. However, the three features from original train dataset do not boost the performance of LightGBM significantly (Appendix XII Figure.3).

According to the time series analysis (Appendix XIII), The number of activated cards raised steeply in 2017 and the impressive amount of sales is tied to three specific time frames -- morning and afternoon (5:00 am~ 5:00 pm EST), Monday and Tuesday and from January to April. 

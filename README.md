# House_Pricing_Prediction
TU/e Data-Driven Course Assignment

![Python](https://img.shields.io/badge/Python-FFD43B?style=for-the-badge&logo=python&logoColor=blue)

## Assignment Overview
The real estate firm aims to forecast the prices of three-bedroom houses for each month spanning January 2020 to July 2022. After exploring the dataset, we used 
- ModelA: Time-independent supervised regression:
  - Random Forest Regression model
  - Rolling window to create subsets without being influenced by the time dimension and capture any possible trends
  - Response features to be devoid of time dependency
  - Cross Validation
  - Mean Absolute Error to check prediction
- ModelB: Time-dependent time series forecasting:
  - Recurrent neural network with LSTM
  - Tune the hyperparameters
 
#### My Role
I am responsible for Model A. 

##### Some analytical pathways and Deliberations Example
###### Response Features
- year
- month
- house type (House or Units)
- bedrooms (from 2 to 6)
- X-Month Rolling Window: average, maximum, minimum, and price difference

###### Window Size (Feature Selection)
After examining the dataset, no evident pricing trends were discerned across various house types and room numbers. Consequently, it becomes imperative to assess the optimal size of rolling windows and determine the ideal duration for calculating average prices, which will contribute to more accurate predictions of future pricing. 

Several potential avenues for exploration have been considered:
- 2 months
- 3 months which could represent a quartile.
- 4 months which could represent a season and means the price would be influenced with a season trend.
- 6 months which could represent a half year and means the price could be predicted by the first half or second half of the year.

The rolling windows selected are:

If the rolling window width is 2:
*   Rolling Mean: The mean price of two consecutive months with same number of bedrooms
    Ex: (02/2011 bedroom:2 + 03/2011 bedroom:2)/2

*   Rolling minimum: The minimum price of two consecutive months with same number of bedrooms
    Ex: 02/2011 bedroom:2 vs 03/2011 bedroom:2

*   Rolling maximum: The maximum price of two consecutive months with same number of bedrooms
    Ex: 02/2011 bedroom:2 vs 03/2011 bedroom:2

*   Rolling difference: The difference price of two consecutive months with same number of bedrooms
    Ex: 03/2011 bedroom:2 - 02/2011 bedroom:2 
        or 01/2012 - 12/2011(cross the year)

## Results
- Leveraging a 2-Month Rolling Window: Maximum, Minimum, and Price Difference Combination could provide the best prediction
- Mean Absolute Error = 127540.0  (Overall Average Price is around 1 million)

##### Model Evaluation
- Measures the average absolute difference between the predicted and actual values
<img width="1046" alt="image" src="https://github.com/yabee111/House_Pricing_Prediction/assets/56541415/95f7de29-e4d9-4724-8123-0b23863e30de">

Considering the price diversity of the houses with 3 bedrooms we can conclude that the model has achieved a fine accuracy in predicting the target variable. The performance of the model was affected by the choice of hyperparameters and the quality of the training data. The feature engineering process was carefully designed to capture the relevant information from the features. The random forest model outperformed other machine learning models and statistical models that were tried in the project, due to its ability to capture complex interactions among the features. Future work could focus on improving the accuracy of the model by further tuning the hyperparameters and exploring other feature engineering techniques.


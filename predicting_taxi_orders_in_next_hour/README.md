# Predicting Taxi Orders in the Following Hour

### Contents
1. [Objectives]()
2. [Data]()
3. [Method and Tools Used]()
4. [Conclusions]()<br />


### Objectives
The Sweet Lift Taxi company needs more drivers during peak hours. It has collected historical data on taxi orders at airports and it wishes to predict the amount of taxi orders for the next hour.

The objective of this project is to train and compare different models with different hyperparameters to make these predictions. The stated aim is to acheive an RMSE metric on the test set of not more than 48.<br />


### Data
|**Data** |  |
|:------------- | :----------|
|datetime | timestamp (to 10 minutes) |
|num_orders | number of orders |


There were 354,369 rows in the dataset.<br />


### Method and Tools Used
***Step 1***: Dealt with null values and anomolies in the data. Removed duplicate rows and variables (columns) not needed for model training.
***Step 2***: Encoding categorical variables using both One Hot Encoding (OHE) and Ordinal Encoding (OE). Split the data into training, validation and test sets.
***Step 3***: Trained Linear, Random Forest and Decision Tree Regression models with data encoded with both OHE and OE. Measured the time to train the model, the time to generate predictions and the RMSE of the predictions. Varied hyperparameters to minimise RMSE.
***Step 4***: Trained 3 gradient boosting algorithms: LightGBM and XGBoost with OHE encoded data and Catboost with unencoded data (Catboost has its own encoding techniques and can handle non-numeric values). Varied hyperparameters and measured the time to train the models and make prediction and the RMSE of the predictions.  Plotted the importance of the features for these 3 models.<br />


### Conclusions
The RMSE of the predictions on the test set data were very similar for the XGBoost and Catboost Regression models, with LGBM close behind. It is likely that with further tuning of the Catboost model parameters, accuracy of that model could be improved further. All three of these gradient boosting models significantly outperformed the models that do not employ gradient boosting.

The Catboost model took the longest to train at 180 seconds, followed by XGBoost at 106. The Random Forest took 22 seconds, but tuning the hyperparameters took much longer. Catboost had a much faster speed of prediction than both XGBoost and LGBM.

For the *LGBM model*, Power was the most important feature followed by Registration Year and then some way behind that was Registration Month.\
For the *XGBoost model*, Power was also the most important feature, followed by Registration month and Registration year which were both similar in importance.\
For the *Catboost model*, Registration Year was the most important feature, followed by 'Power'. Registration month had almost no importance at all.

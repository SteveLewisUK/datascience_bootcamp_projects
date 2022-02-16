# Prediction Models for Used Car Values

### Contents
1. [Objectives](https://github.com/SteveLewisUK/datascience_bootcamp_projects/blob/main/predicting_used_car_values/README.md#objective)
2. [Data](https://github.com/SteveLewisUK/datascience_bootcamp_projects/blob/main/predicting_used_car_values/README.md#data)
3. [Method and Tools Used](https://github.com/SteveLewisUK/datascience_bootcamp_projects/blob/main/predicting_used_car_values/README.md#method-and-tools-used)
4. [Conclusions](https://github.com/SteveLewisUK/datascience_bootcamp_projects/blob/main/predicting_used_car_values/README.md#conclusions)



### Objectives
'Rusty Bargain' is a used car sales service.  In order to attract new customers, it wished to develop an app for customers to quickly find out the market value of their car.

The objective of this project was to train and compare a number of models with various hyperparameters to predict car values.  In particular to compare gradient boosting methods with Linear Regression (as a sanity check), Random Forest Regression and Decision Tree Regression.  The models were to be evaluated according to:
- The time required for training
- The speed of the predictions
- The quality of the predictions (the RMSE metric was used to evaluate the models).



### Data
|**Features** |  |
|:------------- | :----------|
|DateCrawled | Date profile was downloaded from the database|
|VehicleType | Vehicle body type|
|RegistrationYear | Vehicle registration year|
|Gearbox | Gearbox type|
|Power | Power (hp)|
|Model | Vehicle model|
|Mileage | Mileage (measured in km)|
|RegistrationMonth | Vehicle registration month|
|FuelType | Fuel type|
|Brand | Vehicle brand|
|NotRepaired | Vehicle repaired or not|
|DateCreated | Date of profile creation|
|NumberOfPictures | Number of vehicle pictures|
|PostalCode | Postal code of profile owner (user)|
|LastSeen | Date of the last activity of the user|

|**Target** |  |
|:------------- | :----------|
|Price | Price in Euros|

There were 354,369 rows in the dataset.



### Method and Tools Used
***Step 1***: Dealt with null values and anomolies in the data. Removed duplicate rows and variables (columns) not needed for model training.
***Step 2***: Encoding categorical variables using both One Hot Encoding (OHE) and Ordinal Encoding (OE). Split the data into training, validation and test sets.
***Step 3***: Trained Linear, Random Forest and Decision Tree Regression models with data encoded with both OHE and OE. Measured the time to train the model, the time to generate predictions and the RMSE of the predictions. Varied hyperparameters to minimise RMSE.
***Step 4***: Trained 3 gradient boosting algorithms: LightGBM and XGBoost with OHE encoded data and Catboost with unencoded data (Catboost has its own encoding techniques and can handle non-numeric values). Varied hyperparameters and measured the time to train the models and make prediction and the RMSE of the predictions.  Plotted the importance of the features for these 3 models.



### Conclusions
The RMSE of the predictions on the test set data were very similar for the XGBoost and Catboost Regression models, with LGBM close behind. It is likely that with further tuning of the Catboost model parameters, accuracy of that model could be improved further. All three of these gradient boosting models significantly outperformed the models that do not employ gradient boosting.

The Catboost model took the longest to train at 180 seconds, followed by XGBoost at 106. The Random Forest took 22 seconds, but tuning the hyperparameters took much longer. Catboost had a much faster speed of prediction than both XGBoost and LGBM.

For the *LGBM model*, Power was the most important feature followed by Registration Year and then some way behind that was Registration Month.\
For the *XGBoost model*, Power was also the most important feature, followed by Registration month and Registration year which were both similar in importance.\
For the *Catboost model*, Registration Year was the most important feature, followed by 'Power'. Registration month had almost no importance at all.

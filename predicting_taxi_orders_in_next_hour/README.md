# Forecasting Orders for a Taxi Company

### Contents
1. [Objectives](https://github.com/SteveLewisUK/datascience_bootcamp_projects/blob/main/predicting_taxi_orders_in_next_hour/README.md#objectives)
2. [Data](https://github.com/SteveLewisUK/datascience_bootcamp_projects/blob/main/predicting_taxi_orders_in_next_hour/README.md#data)
3. [Method and Tools Used](https://github.com/SteveLewisUK/datascience_bootcamp_projects/tree/main/predicting_taxi_orders_in_next_hour#method-and-tools-used)
4. [Conclusions](https://github.com/SteveLewisUK/datascience_bootcamp_projects/blob/main/predicting_taxi_orders_in_next_hour/README.md#conclusions)<br />


### Objectives
The Sweet Lift Taxi company needed more drivers during peak hours. It collected historical data on taxi orders at airports and it wished to be able to predict the amount of taxi orders for the next hour.

The objective of this project was to train and compare different models with different hyperparameters to make these predictions. The stated aim was to acheive an RMSE metric on the test set of less than 48.<br />


### Data
Time series data was available as follows:
|**Feature** | **Description** |
|:------------- | :----------|
|datetime | Timestamp (accurate to 10 minutes) |
|num_orders | The number of orders in the time period |

There were 26,496 rows in the dataset which constitued the 6 month period from March 1 to August 31 2018.<br />


### Method and Tools Used
***Step 1***: Checked the time series data is in chronological order and resampled it from 10 minute intervals to intervals of 1 hour\
***Step 2***: Ran 'differencing' and 'decomposition' checks to ascertain whether the data was stationary, ie had constant mean and variance.  This is a requirement for training models\
***Step 3***: Created new features from the data with which to train the models: Datetime features, Lagged features, Rolling window statistics, Expanding window statistics\
***Step 4***: Split the data into training, validation and test sets without shuffling and trained Linear, Decision Tree and Random Forest Regression models. Varied hyperparameters to minimise RMSE\
***Step 5***: Trained two models that use Gradient Boosting: XGBoost and Catboost and plot the importance of the features in the models\
***Step 5***: Compared how each of the models performed on the test set data.<br />


### Conclusions
The Random Forest Regression model performed best on the test set data with an RMSE acheived of 45.78 (which was under the specified threshold of 48).

Although the Catboost Regressor performed best on the validation set, the RMSE on the test set was not under the specified threshold. However, it is possible both the XGBoost and Catboost models could be improved with additional hyper-parameter training.

For the *XGBoost model* the most important feature in the model was the hour, the next important the previous hour and then the previous 2 hours.\
For the *Catboost model* the hour was by far the most important feature in the model, much more important than all the other features.

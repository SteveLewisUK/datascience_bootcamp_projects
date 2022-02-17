# Identifying Patterns in Video Game Sales

### Contents
1. [Objectives]()
2. [Data]()
3. [Method and Tools Used]()
4. [Conclusions]()<br />


### Objectives
The online store *Ice* sells video games worldwide. User and expert reviews, genres, platforms (e.g. Xbox or PlayStation) and historical data on game sales are available from open sources. The company wished to identify patterns that determine whether a game succeeds or not. This will allow it to spot potential big winners and plan advertising campaigns.

The objective of this project was to carry out a preliminary analysis of historical data on game sales. It is December 2016 and the company was planning a campaign for 2017.<br />


### Data
|**Feature** | **Description** |
|:---------------|:-----------------|
| Name  |     |
|Platform          |                          |
| Year_of_Release      |                     |
| Genre                |                     |
| NA_sales             | North American sales in USD million |
| EU_sales             | European sales in USD million       |
| JP_sales              | Sales in Japan in USD million      |
| Other_sales  |    (sales in other countries in USD million)    |
| Critic_Score     |   maximum of 100   |
| User_Score     |   maximum of 10    |
| Rating     |  The Entertainment Software Rating Board (ESRB) evaluates a game's content and assigns an age-based rating such as Teen or Mature   |

There were 16,715 rows in the dataset.  Data for 2016 may be incomplete<br />


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


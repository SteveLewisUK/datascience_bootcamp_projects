# Predicting Customer Churn for a Telecoms Company

### Contents
1. [Objectives](https://github.com/SteveLewisUK/datascience_bootcamp_projects/tree/main/predicting_subscription_churn#objectives)
2. [Data](https://github.com/SteveLewisUK/datascience_bootcamp_projects/tree/main/predicting_subscription_churn#data)
3. [Method and Tools Used](https://github.com/SteveLewisUK/datascience_bootcamp_projects/tree/main/predicting_subscription_churn#method-and-tools-used)
4. [Conclusions](https://github.com/SteveLewisUK/datascience_bootcamp_projects/tree/main/predicting_subscription_churn#conclusions)<br />


### Objectives
The telecom operator Interconnect wanted to be able to forecast client churn. If it was discovered that a user was planning to leave, they would be offered promotional codes and special plan options.

Interconnect mainly provides two types of services:
1.	Landline Communications, where phones can be connected to several lines simultaneously.
2.	Internet Connectivity. The network can be set up via a telephone line (DSL, digital subscriber line) or through a fiber optic cable.

Other services the company provides include:
- Internet Security: Antivirus software and a malicious website blocker
- A dedicated technical support line
- Cloud file storage and data backup
- TV and movie streaming.

Clients had 3 payment options: Pay Monthly or sign a 1- or 2-year contract. They could use various payment methods and receive an electronic invoice after a transaction.

Interconnect's marketing team collected customer data including personal information and information about their plans and contracts. 

The objective of this project was to use the company's data to train and compare models to forecast whether users were likely to churn or not. Models were to be rated and compared according to their Accuracy and their AUC-ROC Scores.<br />


### Data
The data was contained in 4 separate files, as follows:

|**File** | **Description** | No of Rows | 
|:------------- | :----------| :----------:|
|Contract Information | Included Contract Start Date, Contract End Date, Contract Type and Monthly Charges| 7043 |
|Personal Data | Included Customer Demographic Information| 7043 |
|Internet Services | Information about the Internet services consumed by Customers| 5517 |
|Telephone Services | Information about the Telephone services consumed by Customers| 6361 |
<br />


### Method and Tools Used
***Step 1***: Pre-processed the Data; parsed dates and calculated contract lengths. Created a target column (churn or not) and removed information where required. Joined all 4 datasets\
***Step 2***: Exploratory Data Analysis; investigated and plotted the distribution of monthly charges and contract length for each of the 3 contract types\
***Step 3***: Prepared the data for training models: encoded categorical variables using 'One Hot Encoding'; split into training (75%) and validation (25%) sets; examined the balance of the classes and adjusted them using *upsampling*; standardised the scales using *Standard Scaler*\
***Step 4***: Trained the following models: a Dummy Classifier; Logistic Regression; Decision Tree Classifier (tuning the 'max_depth' hyperparameter); Random Forest Classifier (tuning the 'n_estimators' hyperparameter); Random Forest Classifier with Cross Validation (optimising the number of folds); LGBM Classifier (varying the num_leaves and max_depth parameters)\
***Step 5***: Presented Accuracy and ROC Score for each model. Plotted Confusion Matrix for the model with the highest AUC-ROC.<br />


### Conclusions
The best performing model was the LGBM Classifier with an AUC ROC of 0.9965 and Accuracy of 0.9852. However, the Random Forest Classifier with Cross Validation was a very close second with an AUC ROC of 0.9951 and an Accuracy of 0.9415. 

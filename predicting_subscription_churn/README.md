# Predicting Subscription Churn for a Telecoms Company

### Contents
1. [Objectives]()
2. [Data]()
3. [Method and Tools Used]()
4. [Conclusions]()<br />


### Objectives
The telecom operator Interconnect wanted to be able to forecast client churn. If it was discovered that a user was planning to leave, they would be offered promotional codes and special plan options.

Interconnect mainly provides two types of services:
1.	Landline Communications; where phones can be connected to several lines simultaneously.
2.	Internet Connectivity. The network can be set up via a telephone line (DSL, digital subscriber line) or through a fiber optic cable.

Other services the company provides include:
- Internet security: antivirus software (DeviceProtection) and a malicious website blocker (OnlineSecurity)
- A dedicated technical support line (TechSupport)
- Cloud file storage and data backup (OnlineBackup)
- TV streaming (StreamingTV) and a movie directory (StreamingMovies)

Clients choose to pay monthly or sign a 1- or 2-year contract. They can use various payment methods and receive an electronic invoice after a transaction.

Interconnect's marketing team collected customer data including personal information and information about their plans and contracts. 

The objective of this project was to use that data to train and compare models to forecast users as likely to churn or not.<br />


### Data
The data was contained in 4 separate files, as follows:

|**File** | **Description** | No of Rows | 
|:------------- | :----------|
|Contract Information | included Contract Start Date, Contract End Date, Contract Type and Monthly Charges| 7043 |
|Client's Personal Data | included demographic information| 7043 |
|Internet Services | Information about the Internet services consumed by customers| 5517 |
|Telephone Services | Information about the Telephone services consumed by customers| 6361 |
<br />


### Method and Tools Used
***Step 1***: Exploratory Data Analysis and visualiation; Horizontal Bar Plot, Stacked Bar Plot, KDE Plot (re-indexed axes to account for years with no movies or reviews)\
***Step 2***: Normalised text including using Regular Expressions. Tokenised and Lemmatised text using the NTLK (Natural Language Toolkit) and the SpaCy libraries\
***Step 3***: Converted the text data into numeric data for model training by calculating TF-IDF vectors. Also Vectorised the Test data\
***Step 4***: Trained Logistic Regression model with these TF-IDF values for both the NTLK and the SpaCy data. Trained LGMB Classifier with SpaCy and TF-IDF\
***Step 5***: Used BERT to get Word Embeddings from the texts. Used these to train a further Logistic Regression Model\
***Step 6***: Plotted F1 Score, ROC Curves and Precision/Recall for each model. Compareed models based on F1 Score.<br />


### Conclusions
Both the initial Logistic Regression models (trained on NTLH and ScaCy lemmatised data) performed equally well according to the F1 scores obtained on the test set data.  When tested on additional reviews in the project, the SpaCy model seemed to outperform the NTLK one. However, it took much more time to get the vectors from the text lemmatised with the SpaCy library, than with the NTLK library.

The LGBMClassifier performed less well than expected, though this could be improved potentially with hyper-parameter tuning.

Creating Word Embeddings with BERT is only practical on a GPU. In this project only 200 reviews out of over 47,000 were used to reuce model training time.  However, based on a small test of 10 reviews, many of the predictions seemed accurate.  A few seemed less reasonable, but that was to be expected given the small training set for the Logistic Regression/BERT model. 

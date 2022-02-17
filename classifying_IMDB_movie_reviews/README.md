# Classifying IMDB Movie Reviews

### Contents
1. [Objectives]()
2. [Data]()
3. [Method and Tools Used]()
4. [Conclusions]()<br />


### Objectives
*The Film Junky Union*, a new community for classic movie enthusiasts, is developing a system for filtering and categorizing movie reviews. 

The objective of this project was to train and compare models to classify positive and negative reviews using a dataset of IMBD movie reviews with polarity labelling. The models needs to have an F1 score of at least 0.85.<br />


### Data
The data was provided by Andrew L. Maas, Raymond E. Daly, Peter T. Pham, Dan Huang, Andrew Y. Ng, and Christopher Potts. (2011). Learning Word Vectors for Sentiment Analysis. The 49th Annual Meeting of the Association for Computational Linguistics (ACL 2011).

Here's the description of selected fields:
|**Selected Fields** |  |
|:------------- | :----------|
|tconst | Unique movie identifier|
|start_year | Year of release|
|genres | Genres by which the movie has been classfied|
|start_year | The year of the movie's release|
|review | The text of the review |
|start_year | Year of release|
|pos | The target: '0' for negative and '1' for positive|
|ds_part | 'train' or 'test' for the train or test part of dataset |

There are also other fields in the dataset.
There were 47,331 rows in the dataset.<br />


### Method and Tools Used
***Step 1***: Exploratory Data Analysis and visualiation; Horizontal Bar Plot, Stacked Bar Plot, KDE Plot (re-indexed axes to account for years with no movies or reviews)
***Step 2***: Normalised text including using Regular Expressions. Tokenised and Lemmatised text using the NTLK (Natural Language Toolkit) and the SpaCy libraries
***Step 3***: Converted the text data into numeric data for model training by calculating TF-IDF vectors. Also Vectorised the Test data.
***Step 4***: Trained Logistic Regression model with these TF-IDF values for both the NTLK and the SpaCy data. Trained LGMB Classifier with SpaCy and TF-IDF
***Step 5***: Used BERT to get Word Embeddings from the texts. Used these to train a further Logistic Regression Model
***Step 6***: Plotted F1 Score, ROC Curves and Precision/Recall for each model. Comparede models based on F1 Score.<br />


### Conclusions
Both the initial Logistic Regression models (trained on NTLH and ScaCy lemmatised data) performed equally well according to the F1 scores obtained on the test set data.  When tested on additional reviews in the project, the SpaCy model seemed to outperform the NTLK one. However, it took much more time to get the vectors from the text lemmatised with the SpaCy library, than with the NTLK library.

The LGBMClassifier performed less well than expected, though this could be improved potentially with hyper-parameter tuning.

Creating Word Embeddings with BERT is only practical on a GPU. In this project only 200 reviews out of over 47,000 were used to reuce model training time.  However, based on a small test of 10 reviews, many of the predictions seemed accurate.  A few seemed less reasonable, but that was to be expected given the small training set for the Logistic Regression/BERT model. 

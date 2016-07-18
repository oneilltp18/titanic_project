# Project 5 Titanic Data
### Overview

The goal of this project was to analyze a dataset including information on passengers on the Titanic to see if they survived or not.

I first imported the dataset by connecting to the remote psql database and then used SQLAlchemy and Pandas to create a dataframe of all the information. After that I did some data cleaning to get myself in a position where I had a clean dataframe to perform analysis on. I created some dummy columns, checked for and dealt with null values, along with a few other data cleaning techniques.

Once I had a clean dataframe, I moved on to the analysis portion of the project. I made a few different model types (Logistic Regression, KNN, Decision Tree) and used some model enhancement techniques (GridSearch, Cross Validation, Train Test Split, Bagging) to create the best model possible.

# Findings

I found that most of my accuracy scores for my models sat right around .79. My second best score was acquired when I performed a gridsearch on my KNN model, found the ideal parameters, re-instantiated the KNN model with those parameters, and then tested that with 5-fold cross validation. This gave me an accuracy score of .809.

My Best score was acquired when I performed a gridsearch on my Decision Tree Classifier to find the ideal Parameters. When I performed the gridsearch, I printed out ".best_score_" to see what my most accurate model in that run-through was and got a score of .813. The parameters I was iterating over for the gridsearch were "n estimators", "max samples", and "max features". This was my best accuracy score for the project.

One curious result was when I was performing the analysis with bagging on my decision tree model. Once I found the ideal parameters for my decision tree model, I then performed a grid search to find the best parameters for the bagging classifier as well. Once I ran a model with ideal Decision Tree parameters combined with ideal Bagging Classifier parameters, my accuracy score dropped down to around .73. This was my lowest score of the project.

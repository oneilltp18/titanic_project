# Project 5 Titanic Data
### Overview

The goal of this project was to analyze a dataset with information on passengers of the Titanic, and then to create a model that would predict whether or not they survived the disaster.  

I first imported the dataset by connecting to the remote postgreSQL database and then used SQLAlchemy and Pandas to create a dataframe of all the information. After some extensive cleaning, I was in a position to begin making a few different models to see how well I could predict the outcome of passengers.  

## Visualization  

During my exploratory Data Analysis I created a few images that I thought did an excellent job illustrating a few trends within the data. These were created using seaborn swarmplots.  

![Gender vs Age](https://raw.githubusercontent.com/oneilltp18/titanic_project/master/visualization/gender_age.png "Gender vs Age")  
The above plot does an excellent job showing the plight of the male passengers as compared to the female passengers aboard the Titanic. You can very clearly see that a massive portion of the male passengers did not survive (noted by the red dot, as opposed to the blue meaning they survived). Of the males that did survive, there is a concentrated clump towards the much lower end of the age spectrum.  

This is a very strong and chilling visualization of the often-quoted phrase "Women and children first."  

![Gender vs Ticket Price](https://raw.githubusercontent.com/oneilltp18/titanic_project/master/visualization/gender_fare.png "Gender vs Ticket Price")  
The above plot is a visualization of Passengers split by gender and sorted by the price of their ticket. The blue dots survived while the red dots did not. We can, again, see very clearly that many more females survived as opposed to males. Digging further, we can also see that as the price of the ticket for the female passengers increased, there seems to be less and less fatalities. One could safely assume wealthy women were among the most likely to survive.  

![Passenger Class vs Age](https://raw.githubusercontent.com/oneilltp18/titanic_project/master/visualization/class_age.png "Passenger Class vs Age")  
Looking at the above plot, which splits the passengers into their class while aboard the Titanic and sorts them by age, it is very easy to see that as you move from 3rd to 1st class, the survival rate increases. Most of the deaths were accounted for by the most-likely poorer 3rd class passengers, with 1st class passengers surviving at a much more substantial rate.

## Findings

The models used for this project were Logistic Regression, KNN, and Decision Tree Classifier.

In terms of quantifying performance for these classifications, I based my overall decision on AUC scores for the different model types. The scores achieved were as follows:  
* auc for logistic model is:  0.895997239476
* auc for knn model is:  0.914078674948
* auc for decision tree is:  0.886335403727

![Roc Curves](https://raw.githubusercontent.com/oneilltp18/titanic_project/master/visualization/roc_curves.png "Roc Curves")

As you can see, my best AUC scores were achieved with the KNN model and the Logistic Regression model. For all three estimators, a gridsearch was performed to find the optimal parameters, and those parameters were used to create the model that output the predictions.

As a bonus, I tried out a Bagging Classifier on my ideal Decision Tree model to see how that would affect things. Overall, when I acquired a score through cross-validation and taking the mean of the accuracy score for each of my 5 total folds, the scores were much worse for the grid-searched bagging classifier than with the simple decision tree. Something curious was happening, however. When I simply used a default bagging classifier with a Decision Tree as the base estimator, I was getting cross validation scores very similar to those of the decision tree itself, but when I gridsearched over different Bagging Classifier parameters, I ended up getting much worse scores (around .8 compared to around .69). What makes this even more curious is that the base parameters that resulted in a cross validation score very similar to the Decision Tree model were searched during my gridsearch, but still the scores came out much worse. This is certainly something to dig deeper into.  

# Results Summarized  
Judging by AUC Scores, **KNN and Logistic Regression performed best with scores of .914 and .896 respectively.**   

Judging by Accuracy Scores, **KNN performed best with an Accuracy Score of .81, or 81% accuracy** at predicting whether a passenger survived or not. **Decision Tree Classifier was close behind with an 80% accuracy.**

Based on these results, I would choose to move forward with the KNN (K-nearest neighbors) model.

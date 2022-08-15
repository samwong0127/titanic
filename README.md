# Titanic - Machine Learning from Disaster - kaggle
Kaggle competition: Titanic - Machine Learning from Disaster

**Aim**: To use machine learning to create a model that predicts which passengers survived the Titanic shipwreck.

This is the repo of the contruction of ML models for the competition. *data* folder contains the test and train data given. *predictions* folder contains the predictions on test data by different models and entries. *titanic- one-hot encoding.ipynb* is the Jupyter Notebook for a small EDA, feature extraction, feature engineering, and training of ML models. It also contains my thinking process and draft of training


### This repo is finialised on 12th Aug, 2022. The final notebook can be seen on [https://www.kaggle.com/code/samwong127/titanic-survival-rate-with-sklearn].


### Conclusion and knowledge
In this competition, the predictions with highest score (**0.78708**) comes from ***Logistic Regression*** (LR). ***Guassian Process Classifier*** (GPC) has the highest accuracy in the training set but LR gets the highest score in the test set. Therefore, overfitting may be occured in the former model. Besides, both models have higher f1-score in predicting **0 (Not Survived)** than **1 (Survived)**. One reason is that the total number of survivors is less than that of deaths in the training set. When predicting the deaths, LR has higher precision but lower recall than GPC. When predicting the survived, LR has lower precision but higher recall than GPC.
Overall, Guassian Process Classifier is better in predicting "Not Survived" (0.9 > 0.89) and Logistic Regression is better in predicting "Surivived" (0.82 > 0.8).

Things I learnt:
1. Ways of Feature engineering: Transforming the number of Siblings and Parent/Child into whether he has a sibling and Parent/Child, from numerical features to categorical features (Ticket class)
2. Feature extraction: Extracting the title from name, Cabin class from Cabin ID, 

### Prediction Diary

1, 2: 0 (Codes corrupted)

5: 0.77990 (Rank 3311/14085 Date: 23/6/2022)
1. Null -> median(Age, Fare), mode (Embarked)
2. Features used: Pclass, Sex, Age, SibSp, Parch, Fare, Embarked, Title, IsMs,  IsAlone Categorical data -> One-hot encoding(Pclass, Embarked, Title)
3. MinMax scaled 
4. Outliers in Fare and FamilySize are removed 
5. SVC is used


6_logR: 0.78229 (Rank 2951/15098 Date: 12/6/2022)
Differences with prediction 5:
1. SibSp and Parch -> hasSibSp and hasParch
2. Not scaled 
3. Logsitic Regression used

7_logR: 0.78708 (Rank 1898/15110 Date: 12/6/2022)
Differences with prediction 5:
1. SibSp and Parch -> hasSibSp and hasParch
2. MinMaxScaler scaled 
3. Logsitic Regression used

8_gpc: 0.77990
Differences with prediction 7:
1. Added CabinS as feature (A, B, C, ..., N)


Ideas on categorical feature with a large set of categories (feature1: {A, B, C, ...})

Get the correlation on each categories with target

Assgin larger index on higher correlation

If A has highest correlation with the target, A set as 10000 (for example)
Then, B: 1000, C: 100 etc.

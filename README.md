# titanic
Kaggle competition: Titanic - Machine Learning from Disaster

**Aim**: To use machine learning to create a model that predicts which passengers survived the Titanic shipwreck.

This is the repo of the contruction of ML models for the competition. *data* folder contains the test and train data given. *predictions* folder contains the predictions on test data by different models and entries. *titanic- one-hot encoding.ipynb* is the Jupyter Notebook for a small EDA, feature extraction, feature engineering, and training of ML models.


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

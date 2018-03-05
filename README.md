# Classification on Orange data

Data from KDD CUP 2009 provided by telecomunication corporation Orange S.A. Data contains 50000 examples and 230 features, the first 190 features are numerical and the last 40 are categorical. The task is to estimate the churn probability of customers (classification problem on unbalanced data). The performance metric is AUC ROC.

The public data was used in Kaggle competition https://www.kaggle.com/c/telecom-clients-churn-prediction/data. The 50000 examples are splitted into train data (40000 examples) and test data (10000 examples). Competitors don't have access to the test labels so the test data is not supposed to be used in model fitting, but in performance evaluation.

This is a classification problem on anonymized, unbalanced data with lots of missing values, and there is also a particular interest in finding a measure that reflects the economic impact of ML models.    

## Dataset
Anonymized data on 40000 users with 190 numeric features and 40 categorical features. Data is unbalanced and contains lots of missing values. 
## What was done:
1.	Statistical analysis and visualization
2.	Selection of performance score  
3.	Data preprocessing
4.	Choosing a baseline model from a set of popular classifiers (Logistic regression, Random Forest, Gradient Boosting, Bayes) 
5.	Feature selection 
6.	Model parameters fitting via cross validation 
7.	Model adequacy check on a test set
8.	Analysis of economic impact
### Preprocessing
*	Hashing
* OneHotEncoding
*	Encoding with densities
*	Data scaling
*	Filling missing values
*	Rebalancing
### Performance Score
AUC ROC was used as performance score, as it reflects TPR and FPR. TPR is important for understanding how many churn users are identified and FPR is related to the economical impact (retention is costly).
Baseline modeling:
Several algorithms were used: Lasso and Ridge Regression, Random Forest, Gradient Boosting, kNN, Naïve Bayes Classifier. Best result was achieved on Gradient Boosting.

### Feature selection
Correlation with target, Lasso Regression feature selection.
### Model fitting 
Model was fit with 5-fold cross validation using AUC ROC as a performance measure. Baseline model was Gradient Boosting, parameters were categorical features encoding, filling missing values, sample balancing, features selection as well as Gradient Boosting model parameters that were optimized via Grid Search. 
### Best Model
Best preprocessing tactic was to encode categorical features with densities, fill missing values with an outlier value, delete features with >70% of missing values.

Gradient Boosting parameters:
*	loss: ‘deviance’
*	learning_rate: 0.03
*	n_estimators: 450
*	max_depth: 3
### Further Research
*	Feature engineering 
*	Using of model ensemble
*	Manage outliers in numerical features

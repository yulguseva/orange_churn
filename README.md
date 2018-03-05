# Classification on Orange data

## Dataset
Original dataset from KDD CUP 2009 provided by telecomunication corporation Orange S.A. http://www.kdd.org/kdd-cup/view/kdd-cup-2009/Intro . The public data was used in Kaggle competition https://www.kaggle.com/c/telecom-clients-churn-prediction/data. Data contains 50000 examples and 230 features, the first 190 features are numerical and the last 40 are categorical. The task is to estimate the churn probability of customers (probability of moving out of company's service over a specific period of time). The performance metric is AUC ROC. The data is splitted into train data (40000 examples with labels) and test data (10000 examples without labels), test data was used for competition purposes on Kaggle.com.

## Problem
This is a classification problem on anonymized, unbalanced data with lots of missing values and there is also a particular interest in finding a measure that reflects the economic impact of ML models.    


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
*	Weighting
### Performance Score
AUC ROC was used as performance score, as it reflects TPR and FPR. TPR is important for understanding how many churn users are identified and FPR is related to the economical impact (retention is costly).
Baseline model:
Baseline model was chosen among several algorithms from sklearn library, such as Logistic regression, Random Forest, Gradient Boosting and Naïve Bayes classifiers. Best result was achieved on Gradient Boosting classifier.

### Feature selection
Feature selection using VarianceThreshold, Lasso regression, SVM and Extremely Randomized Trees.
### Model fitting 
Model was fit with 5-fold cross validation using AUC ROC as a performance measure. Baseline model results were improved by  varying preprocessing techniques and optimizing model parameters via Grid Search. 
### Best Model
Optimal preprocessing included:
* encoding categorical features with frequencies
* filling missing values in categorical features with zeros
* filling missing values in numerical features with max + 1
* removal of empty and almost emrty features (>70% of missing values)
* feature selection using Lasso regeresiion with regularization coefficient of 0.0025.

Optimal GradientBoostingClassifier parameters:
*	loss: ‘deviance’
*	learning_rate: 0.03
*	n_estimators: 450
*	max_depth: 3
### Further Research
*	Feature engineering 
*	Ensembling different models and making meta-models
*	Manage outliers in numerical features

# Predicting Employee Attrition


## NON-TECHNICAL EXPLANATION OF YOUR PROJECT
100 words to explain what your project is about to a general audience. 

## DATA
Due to the confidential nature of the data required, I have decided to use a publicly available dataset that was prepared by IBM and shared through Kaggle. The dataset consists of 1,400 records containing employee information. Input variables relate to personal information, salary and role/position, work environment, employee performance, etc. The output is a binary yes/no variable (attrition) that classifies whether a given employee has left or stayed in the company.

## MODEL 
Given the need to have a model that is highly explainable due to the highly-sensitive nature of employee personal data being used and the potential decisions impacting employees that would arise from use this model,  Decision Trees and Logistic Regression were used as models. In adittion, SVMs were also used - although less explainable, can work well with non-linear problems.

## HYPERPARAMETER OPTIMSATION
Below the hyperparameters used in each model. Gridsearch combined with crossvalidation (sklearn GridSearchCV) was the method used to optimise hyperparameters.
- Logistic Regression - regularization C, penalty
- SVM - regularization C, kernel, gamma
- Random Forest - number of estimators (trees), max tree depth, minimum leaf samples
- Gradient Boosting - number of estimators (trees), max tree depth, minimum leaf samples, learning rate

## RESULTS
A summary of your results and what you can learn from your model 


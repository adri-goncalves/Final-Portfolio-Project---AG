# PREDICTING EMPLOYEE ATTRITION


## NON-TECHNICAL EXPLANATION OF YOUR PROJECT
This project is a first step at attempting to predict whether a given employee is/is not likely to leave the organization (Yes/No classification problem). It currently leverages employee data created by IBM to get started with modelling. The model assesses existing fields (columns) and conducts some data preparation/clean-up (e.g. removing redundant columns). It then uses the dataset to train a model that can then be used to predicting employee attrition as well as providing a view of variables by predicting importance. This tool should be a great source to support HR teams involved with employee retention designing their programs/strategies/policies. Note this is still a preliminary version that requires further refining. 

## DATA
Due to the confidential nature of the data required, I have decided to use a publicly available dataset that was prepared by IBM and shared through Kaggle. The dataset consists of 1,400 records containing employee information. Input variables relate to personal information, salary and role/position, work environment, employee performance, etc. The output is a binary yes/no variable (attrition) that classifies whether a given employee has left or stayed in the company.

## MODEL 
Given the need to have a model that is highly explainable due to the highly-sensitive nature of employee personal data being used and the potential decisions impacting employees that would arise from use this model,  Decision Trees and Logistic Regression were used as models. In adition, SVMs were also used - although less explainable, can work well with non-linear problems.

## HYPERPARAMETER OPTIMSATION
Below the hyperparameters used in each model. Gridsearch combined with crossvalidation (sklearn GridSearchCV) was the method used to optimise hyperparameters.
- Logistic Regression - regularization C, penalty
- SVM - regularization C, kernel, gamma
- Random Forest - number of estimators (trees), max tree depth, minimum leaf samples
- Gradient Boosting - number of estimators (trees), max tree depth, minimum leaf samples, learning rate

## RESULTS AND FUTURE DEVELOPMENT
- Logistic regression, SVM and Decision Trees (Random Forest and Gradient Boosting) modelled and tuned based on a range of 2-4 hyperparameters based aiming at maximizing models F1 scores (weighted). F1 score (weighted) was used as performance metric as it accounts for precision and recall in a situation of class imbalance. Accuracy would not be an appropriate metric as it is typically used in situations where both classes have equal importance, whereas in attrition prediction we are interested in predicting outcomes associated with the minority class (meaning Attrition = 1 / Yes)
- Out of the models tested, the best performing model turned out to be the logistic regression with an F1 score of 0.54 (the simplest of the 3 models tested). This is rather surprising, as one would have expect that this problem involves non-linear relationships among variables, where tree ensembles tend to perform better.
- Having said that, an F1 score is still rather low for what it would be considered good enough model performance (say >0.70). This can be for 2 main reasons: (1) Feature selection would need to be refined. As a next step, one would now deep-dive into the Feature Importance analysis and assess what features are relevant, remove redundant ones and work with the business to enrich the data set with new variables, and (2) the data set is rather small - 1,400 records with class 1 only accounting for 16% of the total. It would be appropriate to collect more data as the models would benefit for training with larger datasets. Acting on (1) and (2) would potentially bring F1 score higher, especially for the decision tree models.
- Looking at confusion matrixes of the different models, the Logistic Regression does a better job at classifying a higher number of true positives, while reducing the number of False Negatives, which in this scenario one would want to minimize. However, the trade-off is that this result is achieved at the expense of a larger number of False Positives. While the model can still be improved and both precision and recall can be refined, in a scenario where this trade-off remains, it will come down to a business decision to define the level of False Positives that would be acceptable to ensure high risk profiles are identified.
- As the model is further refined, it would be ideally to move away from the existing dataset and introduce real company data

# Model Card

Due to the confidential nature of the data required, I have decided to use a publicly available dataset that was prepared by IBM and shared through Kaggle. The dataset consists of 1,400 records containing employee information. Input variables relate to personal information, salary and role/position, work environment, employee performance, etc. The output is a binary yes/no variable (attrition) that classifies whether a given employee has left or stayed in the company.

## Model Description

**Input:** Model uses 34 input variables related to personal information, salary and role/position, work environment, employee performance, etc. See below a selection:
- Personal: Age, Distance from Home, Education (1 to 4), Education Field (categorical), Gender (Male/Female)
- Role related: Department (categorical) Overtime (Yes/No), Business Travel (No, rarely, frequently), Daily rate, Hourly rate, Job level (1 to 4), Job role (categorical)
- Satisfaction: WorkLifeBalance (1 to 4), Environment Satisfaction (1 to 4), Relationship Satisfaction (1 to 4)

**Output:** The output is a binary yes/no variable (attrition) that classifies whether a given employee has left or stayed in the company.

**Model Architecture:** 
- Encoding used to convert categorical into numerical variables (label encoder and get.dummies were used)
- Scaling: MinMaxScaler used to scale all variables between 0 and 1
- Dataset split into 20% test / 80% train-validation. Stratify / balanced parameters were used to ensure models were trained and assessed based on the proportions of the output variable in the original dataset (dataset is unbalanced and target variable class 1 is the class of interest and the minor one - only 16% representation)
- Models trained using cross validation (5 splits) in combination with hyperparameter tunning for the 3 models below. Gridsearch (sklearn GridSearchCV) was the method used to optimise hyperparameters.
  - Logistic Regression - regularization C, penalty
  - SVM - regularization C, kernel, gamma
  - Random Forest - number of estimators (trees), max tree depth, minimum leaf samples
  - Gradient Boosting - number of estimators (trees), max tree depth, minimum leaf samples, learning rate

## Performance
- Model hyperparameters tuned to maximize F1 scores (weighted). F1 score (weighted) was used as performance metric as it accounts for precision and recall in a situation of class imbalance. Accuracy would not be an appropriate metric as it is typically used in situations where both classes have equal importance, whereas in attrition prediction we are interested in predicting outcomes associated with the minority class (meaning Attrition = 1 / Yes)
- Out of the models tested, the best performing model turned out to be the logistic regression with an F1 score of 0.54 for class 1 (the simplest of the 3 models tested). This is rather surprising, as one would have expect that this problem involves non-linear relationships among variables, where tree ensembles tend to perform better.
- Looking at confusion matrixes of the different models, the Logistic Regression does a better job at classifying a higher number of true positives, while reducing the number of False Negatives, which in this scenario one would want to minimize. However, the trade-off is that this result is achieved at the expense of a larger number of False Positives. While the model can still be improved and both precision and recall can be refined, in a scenario where this trade-off remains, it will come down to a business decision to define the level of False Positives that would be acceptable to ensure high risk profiles are identified.

## Limitations
- F1 score for Class 1 is still rather low for what it would be considered good enough model performance (say >0.70). This can be for 2 main reasons: (1) Feature selection would need to be refined. As a next step, one would now deep-dive into the Feature Importance analysis and assess what features are relevant, remove redundant ones and work with the business to enrich the data set with new variables, and (2) the data set is rather small - 1,400 records with class 1 only accounting for 16% of the total. It would be appropriate to collect more data as the models would benefit for training with larger datasets. Acting on (1) and (2) would potentially bring F1 score higher, especially for the decision tree models.
- As the model is further refined, it would be ideally to move away from the existing dataset and introduce real company data
- Additional analysis required to identify potential biases in the data, and adjust the model (eg. dataset split process) to account for this 

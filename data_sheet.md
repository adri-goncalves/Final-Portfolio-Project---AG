# Datasheet Template

## Motivation
- This dataset was created to enable Data Science practitioners  conduct analyses and modelling on HR related topics.
- This is a publicly available dataset, created by IBM and can be found here: https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset/data


## Composition
- The dataset is in a structured, tabular form composed of 1,400 employee records, containing 34 input variables and 1 binary output variable Attrition (Yes/No)
- Given this data was artificial created, there are no inherent issues with data confidentiality. Once the model is refined to incorporate actual real data from employees, then data confidentiality measures and GDPR implications need to be taken into consideration


## Collection process
- Data has been created by IBM and extracted from the Kaggle link above.


## Preprocessing/cleaning/labelling
- Data was already pre-labelled
- Upon inspection, there are no missing values or evident outliers. There are some redundant columns (with 1 unique value) that have been removed for the purpose of modelling
- Data encoding to transform categorical into numerical variables and scaling (min/max) was conducted prior to training

 
## Uses
- This data set provides generic employee information from personal, to work environment, performance, salary, etc. The dataset can be used in a variety of HR analytics use cases
- Deeper analysis would be required in order to test model performance against potential biases (e.g. gender). Based on variables that might introduce potential biases, dataset splitting and cross validation should be conducted taking such elements into consideration (e.g. maintaining gender proportions).


## Distribution
- Open license, https://opendatacommons.org/licenses/dbcl/1-0/

## Maintenance
- Data set is static, not currently being maintained

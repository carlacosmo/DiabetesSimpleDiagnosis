# Diabetes Simple Diagnosis
Repository created for **[validation of a Machine Learning model that predicts the diagnosis of diabetes](https://github.com/carlacosmo/DiabetesSimpleDiagnosis/blob/ae5fae7a10385eed7d2959a583db32e17b80f282/diabetes-simple-diagnosis-model-validation.ipynb)** in patients.


## Part 1

In the first stage, **exploratory analysis** is a general analysis of the dataset to understand all the information we have available in the database.
- Alteration in the name of the ID column.
- Validation of the types of variables in the data set.
- Validation if there are null values in the base.
- Validation of the dataset size, number of rows and columns.
- And also validation of the cardinality of the variables, especially the categorical variables.


## Part 2

In the second stage, **data pre-processing**, the database was treated in such a way that it was as compatible as possible for Machine Learning models.The closer the dataset is to the low-level language, the better it will be interpreted by the model and the better the final result will be.
- Treatment of the Gender column, applying the get_dummies() method, which directly transforms categorical variables.
- Normalization of the columns 'Age','BMI','FBS','HbA1c_level' using the RobustScaler() method
- Definition of variables, target and explanatory, that will be used by the model.

Explanatory variables: ‘High_BP’, ‘Smoking’, ‘Female’, ‘Male’, ‘Other’, ‘Age_scaler’, ‘BMI_scaler’, FBS_scaler’, ‘HbA1c_level_scaler’.


## Part 3

**Model training stage**, different models were trained using the **Decision Tree, KNN and Logistic Regression** algorithms. The performance metric used to measure the results of the models was **accuracy**.

You can check out more about accuracy and the main performance metrics for classification models in **[this article I wrote on Medium](https://medium.com/@carlacosmo/performance-metrics-in-machine-learning-classification-models-76a4565e01ff).**

The results were: 
- Decision Tree:0.9410
- KKN: 0.9550
- Logistic Regression: 0.9538


## Part 4

The dataset is analyzed again to see if there is anything that can be changed to further **improve the results**. There is a small correlation between the Age variable and the target variable.Older patients are more likely to have a positive diabetes diagnosis than younger patients.

The Age_scaler column is replaced by the new column that is based on the patient's age group, dividing by classes from 0 to 4, the younger the age the closer it will be to zero, and the older the age the closer it will be to 4.

Explanatory variables: ‘High_BP’, ‘Smoking’, ‘Female’, ‘Male’, ‘Other’, ‘BMI_scaler’, FBS_scaler’, ‘HbA1c_level_scaler’, ‘Age_range’.

The results were: 
- Decision Tree:0.9516
- KKN: 0.9523
- Logistic Regression: 0.9523

There was an improvement in the Decision Tree model but there was a worsening in the other two models.


## Part 5

Again the dataset will be analyzed to see if we can **identify another opportunity**. The BMI (Body Mass Index) variable has a good correction with the target variable. Patients with BMI above 30 are considered diabetic.

The BMI_scaler variable is replaced by a new column that has a value of 1 for patients with a BMI above 30, and a value of 0 for values below 30.

Explanatory variables: ‘High_BP’, ‘Smoking’, ‘Female’, ‘Male’, ‘Other’, FBS_scaler’, ‘HbA1c_level_scaler’, ‘Age_range’,’BMI_range’.

The results were: 
- Decision Tree:0.9619
- KKN: 0.9562
- Logistic Regression: 0.9516

**The Decision tree model had an improvement of almost 1% in its results**. And the other models maintained the same results as the first training, around 95%. 

This last decision tree model was chosen to predict the test base. In this prediction, the test base had a result of 0.9643. **A result of 96% and a result very similar to the result of the validation base.**


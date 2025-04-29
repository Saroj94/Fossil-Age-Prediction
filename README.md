# 📍**Fossil Age Prediction**

## ✅**Problem Statement**
Develop a machine learning model to accurately predict the age of fossils using morphological, stratigraphic, and geological features, providing a fast and reliable alternative to traditional dating methods.

## ✅Objective
Given a dataset containing various fossil features — including morphological measurements, stratigraphic information, and geological indicators — the goal is to develop and evaluate machine learning models capable of accurately predicting the age of fossils.

## 🔴Dataset Description
## **Data Source**
 The initial data was sourced primarily from PaleoBioDB, with additional private sources contributing to the dataset. And publically uploaded in kaggle for research and development perspective.

## ⛓️**How I engineer data pipelines**
1. I collected data from Kaggle
2. Instead of storing data into the local folder, I used Microsof SQL Server to store data and access from it.
2. Setup the connection using dependencies as follows:
    - SQLAlchemy: To create the engine in working space that help in establishing the connection with database through connection string.
    - pyodbc: I used ODBC Driver 18 for SQL Server while establishing the connection with database.
    - pandas: Used pd.read_sql() method to read the table from database.

## 📙**Dataset Description**
1. Fossil dataset with 12 features and 4398 records.
2. There were 3 types of datatypes:
    - Continuous and Discrete (Numerical)
    - Categorical (Object)
    - Boolean (True/False)
3. 8 of them are numerical, 4 of them are categorical and 1 is boolean type data.

## ⏳**Data Preprocessing**
1. Check missing values: No missing value found.
2. Check duplicate values: No duplicated value found.
4. Summary Statistics claculated for numerical features and i found:
    - All Numerical features have approximately same values for **Mean** and **Median** (i.e **Mean** ≈ **Median**) which was the indication of  data is symmetric (normal) except **stratigraphic_layer_depth**. But, other analysis help me to varify whether it is a skewness variation or something else.
    - **Mean** = 152.83
    - **Median** = 146.0
    - **Mean** > **Median** which means data seems like a right-skewed.
    - **Minimum & Maximum** values for some features seems too far leading to outlier problem through summary stats but yet not confirm.
5. Perform **skewness** check analysis such as:
    - skew(): calculate the skewness values of each numerical feature using pandas skew() method and found the skewness values appearently less than 0.5 which is consider as good sign in statistics. This confirm that the feature **stratigraphic_layer_depth** has no problem of skewness.
6. Perform **Outlier** check analysis such as:
    - **Kurtosis**: 
        **Parameter Used**
        - fisher=True means 0 = normal distribution, if it is close to 0 then no need to take any action.
        - fisher=False means 3 = normal distribution, if it is close to 3 then not required any action.
        I found the value of kurtosis close to 3 which again consider as normal in statistics. so no such serious Outliers in the dataset.
    - **Boxplot**: No extreme outliers.

## 📊**Exploratory Data Analysis (EDA)**
1. **Univariate Analysis**
    - Datapoints distribution for all feature seems normal distribution.
    - Count of Sandstone followed by limestone of sorrounding rock type feature is maximum.
    - Geological periods such as Cambrian,Triassic and Cretaceous has maximum count in the dataset.
    - Maximu count of bottom layer of the **stratigraphic_position** where most of the fossils found.
2. **Bivariate Anlaysis**
    - A strong correlation between **uranium_lead_ratio** and **age**.
    - Also followed by **stratigraphic layer depth**, even it is correlated with **Age**

## 🛠️**Feature Encoding**
1. Perform LabelEncoding
2. Perform OneHotEncoding for categorical values
3. Hard coded for Boolean feature

## ⚔️**Feature Scaling**
1. **StanderScaler**

## 🧮**Model Building**
1. Experiment with multiple Machine Learning Algorithms as follows:
    - **Random Forest Regressor**
    - **Decision Tree Regressor**
    - **Gradient Boosting Regressor**
    - **AdaBoost Regressor**
    - **Linear Regressor**
    - **SVM Regressor**
    - **XGBoost Regressor**
    - **KNeighbors Regressor**

## 🪛Model Evaluation
1. Metrices used to evaluate trained models:
    - MSE Score: Mean Square Error
    - MAE score: Mean Absolute Error
    - R2 Score: R-Squared 
    - RMSE Score: Root Mean Squared Error
2. **Gradient Boosting Regressor** Perform well in comparision with others.

## ⚙️**Hyperparameter Tunning**
Best performing parameters found from hyperparameter tunning:
- subsample= 1.0, 
- n_estimators= 400, 
- min_samples_split= 10, 
- min_samples_leaf= 2, 
- max_features= 'sqrt', 
- max_depth= 4, 
- learning_rate= 0.05,
- random_state=42

## 🎯**Future Work** 
- Next I am building a machine learning software for this problem using MLOps concepts
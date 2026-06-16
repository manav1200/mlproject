**Student Performance Prediction**
An end-to-end machine learning web application that predicts a student's math exam score based on demographic and academic factors. 
The project is built around a modular ML pipeline and served through a Flask web interface.

**Problem Statement**
Student performance is shaped by a range of factors beyond academic effort alone parental education level, socioeconomic background, and access to test preparation resources all play a measurable role. This project trains a regression model on those variables to predict math scores, with the broader goal of enabling earlier identification of students who may benefit from additional academic support.

**Tech Stack**
Python 3.8+, FlaskML, Libraries (Scikit-learn, CatBoost, XGBoostData), Pandas, NumPy, Matplotlib, Seaborn, Dill, Notebook, Jupyter

**ML Pipeline**

1. Data Ingestion
The raw dataset is loaded from a CSV file, split into training and test sets, and saved to the artifacts/ directory for use by downstream pipeline components.

2. Data Transformation
A ColumnTransformer pipeline handles all preprocessing before model training.
Numerical features: SimpleImputer with median strategy, followed by StandardScaler
Categorical features: SimpleImputer with most-frequent strategy, followed by OneHotEncoder and StandardScaler
The fitted preprocessor object is serialized and saved as preprocessor.pkl.

3. Model Training
Multiple regression algorithms are trained and evaluated using R2 score. The best-performing model is saved as model.pkl in the artifacts/ directory.

Models evaluated:
Linear Regression
Ridge and Lasso Regression
Random Forest Regressor
Gradient Boosting Regressor
XGBoost Regressor
CatBoost Regressor


4. Prediction

The PredictPipeline class loads the saved preprocessor and model artifacts, transforms the incoming form data, and returns the predicted math score.

# Capstone Project — Cardiovascular Disease Risk Prediction

This repository contains the UC Berkeley AI/ML Capstone project (2025), which explores predicting cardiovascular disease risk from patient clinical and lifestyle features using classical machine learning models.

## Notebook

The full exploratory analysis, feature engineering, modeling, and evaluation are in the Jupyter notebook: `aiml-capstone.ipynb`.

## Project overview

- Goal: Predict whether a patient is at risk of cardiovascular disease (binary classification) using attributes such as age, height, weight, blood pressure, cholesterol, glucose, smoking, alcohol intake, and physical activity.
- Dataset: `data/cardio_train.csv` (original dataset provided alongside the notebook).

## Dataset fields (as used)
- id: unique patient identifier (dropped prior to modeling)
- age: converted from days to `age_years` (integer)
- height (cm)
- weight (kg)
- gender (categorical code)
- systolic_bp (ap_hi)
- diastolic_bp (ap_lo)
- cholesterol (1=normal, 2=above normal, 3=well above normal)
- blood_glucose (gluc: 1=normal, 2=above normal, 3=well above normal)
- smoking (binary)
- alcohol_intake (alco, binary)
- physical_activity (active, binary)
- cardio_disease (target; 0/1)

## Data cleaning & preprocessing (summary)
- Removed rows with non-positive or inconsistent blood pressure values and ensured systolic >= diastolic.
- Filtered out unrealistic heights and weights (height between 50 and 250 cm; weight between 20 and 300 kg).
- Converted age from days to years (`age_years`).
- Dropped duplicate rows and the `id` column.
- Renamed columns for clarity: `age`→`age_years`, `ap_hi`→`systolic_bp`, `ap_lo`→`diastolic_bp`, `gluc`→`blood_glucose`, `alco`→`alcohol_intake`, `smoke`→`smoking`, `active`→`physical_activity`, `cardio`→`cardio_disease`.

## Feature engineering
- BMI computed as weight / (height/100)^2 and added as `bmi`.
- Age groups created and one-hot encoded: `<30`, `30-45`, `45-60`, `60+`.
- One-hot encoding applied to `cholesterol`, `blood_glucose`, and `age_group` (with `drop_first=True`).

## Modeling
- Train/test split: stratified 80/20 split (`random_state=42`).
- Models trained and evaluated in the notebook include Logistic Regression (example run shown), with helper utilities to compute training time and metrics (Accuracy, Precision, Recall, F2 score) and display confusion matrices.
- Additional classifiers imported and available for experiments: SVM (`SVC`), K-Nearest Neighbors (`KNeighborsClassifier`), Decision Tree (`DecisionTreeClassifier`). Grid search (`GridSearchCV`) utilities are included for hyperparameter tuning.

## Evaluation metrics reported
- Accuracy
- Precision
- Recall
- F2 score (beta=2 — emphasizes recall)
- Confusion matrix visualization

## Files in this repo
- `aiml-capstone.ipynb` — full analysis and code
- `data/cardio_train.csv` — dataset used
- `data/cardio_train.xlsx` — alternate dataset format

## Notes & next steps
- Recommended next steps:
  - Fix more data columns like systolic_bp, etc.
  - Try additional models and hyperparameter searches (GridSearchCV) for SVM, KNN, Decision Tree.
  


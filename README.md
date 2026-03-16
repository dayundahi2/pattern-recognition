## Project Overview
This project predicts whether a client will subscribe to a bank term deposit 
using machine learning models.

The dataset contains demographic and economic features, and the target variable 
is whether the client subscribed to the deposit (yes/no).


## Dataset
- Bank Marketing Dataset
- 32,950 training samples
- Target variable: y (yes / no)


## Data Preprocessing

- Removed unnecessary columns: id, contact, day_of_week
- Handled missing values using:
  - SimpleImputer (mode)
  - IterativeImputer
- Applied one-hot encoding to categorical variables
- Removed outliers using IQR method


## Models

We tested several machine learning models:

- Logistic Regression
- Polynomial Model
- Decision Tree
- Ensemble Methods
  - AdaBoost
  - Bagging
  - Gradient Boosting
  - Random Forest
  - XGBoost
  - LightGBM
 

## Results

Best Model: LightGBM

Accuracy: 0.90
F1 Score: 0.94
ROC AUC: 0.78


## Key Findings

Important features include:

- nr.employed
- pdays
- cons.conf.idx

These variables strongly influence the probability of subscription.



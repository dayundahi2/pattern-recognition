# Bank Term Deposit Subscription Prediction

## Project Overview

This project aims to predict whether a client will subscribe to a bank term deposit using machine learning models.
By analyzing the training dataset, we explore how various demographic, economic, and marketing-related features influence the likelihood of subscription.

The goal is to build a predictive model that can classify whether a customer will subscribe to a term deposit (`yes` or `no`).

---

This project predicts whether a bank client will subscribe to a term deposit using machine learning models.

The project demonstrates a full machine learning pipeline including:
- Data preprocessing
- Feature engineering
- Model training
- Model evaluation
- Model comparison

### Project Pipeline

1. Data Exploration
2. Data Preprocessing
3. Feature Engineering
4. Model Training
5. Model Evaluation
6. Model Selection

## Dataset

The dataset contains customer information and economic indicators related to bank marketing campaigns.

Main characteristics:

* Number of training samples: **32,950**
* Target variable: **y (subscription)**

  * `yes` : client subscribed to the term deposit
  * `no` : client did not subscribe

Example features include:

* age
* job
* marital status
* education
* default
* housing loan
* campaign
* pdays
* emp.var.rate
* cons.price.idx
* cons.conf.idx
* euribor3m
* nr.employed

The dataset also shows **significant class imbalance**, where the number of `no` samples is much larger than `yes`.

---

## Data Exploration

We analyzed the distribution of categorical and continuous variables grouped by the target class.

Key observations:

* Customers **above age 61** showed a higher probability of subscription.
* **Lower employment variation rates** correlated with higher subscription probability.
* **Consumer price index and confidence index** also showed relationships with subscription behavior.
* Some variables such as `contact` and `day_of_week` showed little impact on the target variable.

---

## Data Preprocessing

Several preprocessing techniques were applied:

### 1. Variable Selection

Removed columns that had little influence or were unnecessary.

Removed features:

* `id`
* `contact`
* `day_of_week`

---

### 2. Missing Value Handling

Two imputation methods were used:

**SimpleImputer**

* Replaced missing categorical values using the **mode**

**IterativeImputer**

* Used for features with higher missing ratios such as:

  * `default`
  * `education`

---

### 3. Outlier Removal

Outliers were detected using the **IQR method**.

Bounds:

* Lower bound = Q1 − 1.5 × IQR
* Upper bound = Q3 + 1.5 × IQR

Outliers were removed mainly from:

* `cons.conf.idx`

---

### 4. Encoding Categorical Variables

* Binary variables converted to **0 / 1**
* Multi-class categorical variables encoded using **one-hot encoding**

Example:

```
job → job_admin, job_student, job_technician ...
```

Due to class imbalance:

* `yes` was temporarily encoded as **0**
* `no` was encoded as **1**

---

## Model Training

The dataset was split into training and testing sets.

* Train/Test split ratio: **75% / 25%**
* Random state: **100**
* Data shuffled before splitting

We experimented with several models.

---

## Models Tested

### 1. Logistic Regression

Used as a baseline model.

### 2. Polynomial Model

Expanded features to capture nonlinear relationships.

### 3. Decision Tree

Performed better by capturing nonlinear feature interactions.

### 4. Ensemble Methods

Several ensemble techniques were tested:

* AdaBoost
* Bagging
* Gradient Boosting
* Random Forest
* XGBoost
* LightGBM

---

## Model Selection

Performance comparison was conducted using **K-fold cross validation**.

Metrics used:

* Accuracy
* F1 Score
* ROC AUC

Among all models, **LightGBM** showed the best performance.

---

## Final Model Performance

Best model: **LightGBM**

Results:

* Accuracy: **0.90**
* F1 Score: **0.94**
* ROC AUC: **0.78**

Confusion matrix analysis shows that the model effectively identifies customers who are unlikely to subscribe.

---

## Key Features Influencing Prediction

Important variables identified by the models include:

* `nr.employed`
* `pdays`
* `cons.conf.idx`
* `emp.var.rate`

These variables reflect **economic conditions and marketing contact history**, which significantly influence subscription decisions.

---

## Project Structure

```
bank-term-deposit-prediction
│
├── data
│   ├── train.csv
│   └── test.csv
│
├── notebooks
│   └── analysis.ipynb
│
├── src
│   ├── preprocessing.py
│   ├── train_model.py
│   └── evaluation.py
│
├── results
│   └── confusion_matrix.png
│
├── README.md
└── requirements.txt
```

---

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* LightGBM
* Matplotlib
* Seaborn

---

## Conclusion

This project demonstrates the effectiveness of ensemble learning techniques for predicting customer subscription behavior.
Among the tested models, **LightGBM provided the best balance between predictive accuracy and robustness**, especially in handling class imbalance and complex feature interactions.

The insights from this model can help banks **identify potential customers and improve targeted marketing strategies**.


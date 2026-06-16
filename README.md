# Improved Detection of Fraud Cases for E-commerce and Bank Transactions

## Project Overview

Fraud detection is a critical challenge for financial institutions and e-commerce platforms. Fraudulent transactions can lead to significant financial losses, while incorrectly flagging legitimate transactions can negatively impact customer experience and trust.

This project develops machine learning solutions for detecting fraudulent activities across two different transaction environments:

1. **E-commerce Transactions** – Transactions enriched with user behavior, device information, browser details, and geolocation data.
2. **Credit Card Transactions** – Financial transactions with anonymized features transformed using Principal Component Analysis (PCA).

The project follows a complete machine learning workflow including data exploration, preprocessing, feature engineering, class imbalance handling, model training, evaluation, and model selection.

---

## Business Objective

The goal is to build robust fraud detection models that:

* Accurately identify fraudulent transactions.
* Minimize false positives and false negatives.
* Support real-time fraud monitoring and risk management.
* Provide actionable insights into fraud patterns and risk factors.

---

## Datasets

### 1. Fraud_Data.csv

E-commerce transaction data containing:

* User information
* Device information
* Purchase details
* Browser information
* IP address information
* Fraud labels

Target Variable:

* `class`

  * 1 = Fraud
  * 0 = Legitimate

---

### 2. IpAddress_to_Country.csv

IP address mapping dataset used to enrich transaction records with country information.

Fields:

* lower_bound_ip_address
* upper_bound_ip_address
* country

---

### 3. creditcard.csv

Credit card transaction dataset containing anonymized features.

Features:

* Time
* Amount
* V1–V28 (PCA-transformed variables)

Target Variable:

* `Class`

  * 1 = Fraud
  * 0 = Legitimate

---

## Project Structure

```text
project/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   ├── eda_fraud_data.ipynb
│   ├── eda_creditcard.ipynb
│   ├── preprocessing_fraud.ipynb
│   ├── preprocessing_creditcard.ipynb
│   ├── modeling_fraud.ipynb
│   └── modeling_creditcard.ipynb
│
├── models/
│   ├── fraud_random_forest.pkl
│   └── creditcard_random_forest.pkl
│
├── reports/
│
└── README.md
```

---

## Exploratory Data Analysis (EDA)

EDA was conducted separately for both datasets and included:

### Fraud Dataset

* Missing value analysis
* Duplicate detection
* Fraud distribution analysis
* Purchase value analysis
* Age distribution analysis
* Browser and traffic source analysis
* Country-level fraud analysis
* Correlation analysis

### Credit Card Dataset

* Missing value analysis
* Duplicate detection
* Class imbalance analysis
* Distribution of Amount and Time
* PCA feature analysis
* Correlation analysis
* Fraud pattern investigation

---

## Data Preprocessing

### Fraud Dataset

#### Data Cleaning

* Removed duplicate records
* Converted datetime fields to appropriate formats
* Verified data quality and consistency

#### Geolocation Integration

* Converted IP addresses to integer format
* Mapped transactions to countries using IP range matching
* Analyzed fraud distribution by country

#### Feature Engineering

Created the following fraud-related features:

* `time_since_signup`
* `hour_of_day`
* `day_of_week`
* `user_transaction_count`
* `device_transaction_count`

#### Data Transformation

* One-hot encoded categorical variables
* Standardized numerical variables using StandardScaler

#### Class Imbalance Handling

Applied SMOTE (Synthetic Minority Oversampling Technique) on the training dataset to balance fraudulent and legitimate transactions.

---

### Credit Card Dataset

#### Data Cleaning

* Removed duplicate transactions
* Verified data quality

#### Data Transformation

* Standardized numerical features
* Preserved PCA-transformed variables

#### Class Imbalance Handling

Applied SMOTE on the training dataset to address severe class imbalance.

---

## Machine Learning Models

Two classification models were developed and compared for each dataset.

### 1. Logistic Regression

Used as a baseline interpretable model.

Evaluation Metrics:

* F1 Score
* AUC-PR (Area Under Precision-Recall Curve)
* Confusion Matrix
* Classification Report

---

### 2. Random Forest Classifier

Used as an ensemble learning model capable of capturing complex fraud patterns.

Evaluation Metrics:

* F1 Score
* AUC-PR
* Confusion Matrix
* Classification Report

---

## Cross Validation

Stratified K-Fold Cross Validation (k=5) was performed to ensure reliable performance estimation while preserving fraud class distribution across folds.

Metrics Reported:

* Mean F1 Score
* Standard Deviation of F1 Score

---

## Model Selection

Random Forest was selected as the final model for both datasets due to:

* Higher F1 Scores
* Better AUC-PR performance
* Lower false positive rates
* Stronger fraud detection capability
* Consistent cross-validation performance

Final saved models:

* `fraud_random_forest.pkl`
* `creditcard_random_forest.pkl`

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Imbalanced-learn (SMOTE)
* Joblib

---

## Key Outcomes

* Successfully integrated geolocation data into e-commerce transactions.
* Engineered behavioral features associated with fraud risk.
* Addressed severe class imbalance using SMOTE.
* Built and evaluated multiple fraud detection models.
* Identified Random Forest as the best-performing model for both datasets.
* Produced reusable trained models for future deployment and explainability analysis.

---

## Future Work

* Model explainability using SHAP.
* Hyperparameter optimization.
* Real-time fraud detection pipeline.
* Deployment using Flask or FastAPI.
* Model monitoring and drift detection.

---

## Author

Fraud Detection Project – Adey Innovations Inc. Case Study

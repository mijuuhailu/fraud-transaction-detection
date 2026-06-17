# Improved Detection of Fraud Cases for E-commerce and Bank Transactions

## Project Overview

Fraud detection is a critical challenge for both financial institutions and e-commerce platforms. Fraudulent transactions can result in significant financial losses, while incorrectly flagging legitimate transactions can negatively affect customer experience and trust.

This project develops machine learning models capable of detecting fraudulent transactions across two different environments:

1. **E-commerce Transactions** – Rich behavioral data including user activity, device information, browser usage, and geolocation.
2. **Credit Card Transactions** – Financial transaction data containing anonymized PCA-transformed features.

The project follows a complete machine learning pipeline from data exploration and preprocessing to model training, evaluation, and explainability.

---

## Business Objective

The objective is to build reliable fraud detection systems that:

- Accurately identify fraudulent transactions.
- Minimize false positives and false negatives.
- Improve fraud monitoring and risk management.
- Generate actionable business insights from model predictions.

---

## Datasets

### 1. Fraud_Data.csv

E-commerce transaction data containing:

- User information
- Device information
- Browser information
- Purchase information
- IP address information

Target variable:

- `class`
  - 1 = Fraud
  - 0 = Legitimate

---

### 2. IpAddress_to_Country.csv

IP range mapping dataset used to enrich transaction records with country information.

Fields:

- lower_bound_ip_address
- upper_bound_ip_address
- country

---

### 3. creditcard.csv

Credit card transaction data containing:

- Time
- Amount
- V1–V28 (anonymized PCA-transformed features)

Target variable:

- `Class`
  - 1 = Fraud
  - 0 = Legitimate

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
│   ├── modeling_creditcard.ipynb
│   └── shap_analysis.ipynb
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

EDA was conducted separately for both datasets.

### Fraud Dataset

Analysis included:

- Missing value analysis
- Duplicate analysis
- Class distribution analysis
- Purchase value distribution
- Age distribution
- Browser and traffic source analysis
- Country-level fraud investigation
- Correlation analysis

### Credit Card Dataset

Analysis included:

- Missing value analysis
- Duplicate analysis
- Fraud class imbalance investigation
- Amount and Time distributions
- PCA feature exploration
- Correlation analysis

---

## Data Preprocessing

### Fraud Dataset

#### Data Cleaning

- Removed duplicate records
- Converted datetime fields to proper formats
- Verified data quality

#### Geolocation Integration

- Converted IP addresses to integer format
- Mapped transactions to countries using IP range lookup
- Investigated fraud patterns by country

#### Feature Engineering

Created the following features:

- `time_since_signup`
- `hour_of_day`
- `day_of_week`
- `user_transaction_count`
- `device_transaction_count`

#### Data Transformation

- One-hot encoded categorical variables
- Standardized numerical variables using StandardScaler

#### Class Imbalance Handling

Applied SMOTE (Synthetic Minority Oversampling Technique) on the training dataset.

---

### Credit Card Dataset

#### Data Cleaning

- Removed duplicate records
- Verified data consistency

#### Data Transformation

- Standardized numerical features
- Preserved PCA-transformed variables

#### Class Imbalance Handling

Applied SMOTE to balance fraudulent and legitimate transactions in the training set.

---

## Machine Learning Models

Two classification models were trained and evaluated for each dataset.

### Logistic Regression

Used as an interpretable baseline model.

### Random Forest

Used as an ensemble learning model capable of capturing complex fraud patterns.

---

## Model Evaluation Metrics

Models were evaluated using:

- F1 Score
- AUC-PR (Area Under Precision-Recall Curve)
- Confusion Matrix
- Classification Report

These metrics were chosen because fraud detection datasets are highly imbalanced and accuracy alone can be misleading.

---

## Model Results

### Credit Card Dataset

| Model | F1 Score | AUC-PR |
|---------|---------|---------|
| Logistic Regression | 0.10 | 0.677 |
| Random Forest | 0.83 | 0.804 |

**Selected Model:** Random Forest

---

### Fraud Dataset

| Model | F1 Score | AUC-PR |
|---------|---------|---------|
| Logistic Regression | 0.674 | 0.641 |
| Random Forest | 0.696 | 0.704 |

**Selected Model:** Random Forest

---

## Cross Validation

Stratified 5-Fold Cross Validation was performed to evaluate model stability while preserving class distribution.

Evaluation metrics reported:

- Mean F1 Score
- Standard Deviation of F1 Score

---

## Model Explainability

Model interpretation was performed using:

### Built-in Feature Importance

Top fraud indicators identified by the Random Forest model:

1. Device Transaction Count
2. Time Since Signup
3. Day of Week
4. Hour of Day
5. Age
6. Purchase Value

### SHAP Analysis

SHAP was used to:

- Explain global feature importance
- Interpret individual predictions
- Identify drivers of fraud detection
- Support business recommendations

---

## Saved Models

Final trained models were serialized using Joblib:

- `fraud_random_forest.pkl`
- `creditcard_random_forest.pkl`

These models can be reused for inference, deployment, and explainability analysis.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Imbalanced-learn (SMOTE)
- SHAP
- Joblib

---

## Key Findings

- Device activity is the strongest indicator of fraud in e-commerce transactions.
- Transactions occurring shortly after account creation are more likely to be fraudulent.
- Time-based behavioral patterns contribute significantly to fraud detection.
- Random Forest consistently outperformed Logistic Regression across both datasets.
- Feature engineering substantially improved model performance on the fraud dataset.

---

## Future Improvements

- Hyperparameter optimization using GridSearchCV or RandomizedSearchCV
- XGBoost and LightGBM model experimentation
- Real-time fraud detection pipeline
- API deployment using FastAPI
- Model monitoring and drift detection

---


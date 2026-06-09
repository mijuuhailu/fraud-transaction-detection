# Improved Detection of Fraud Cases for E-commerce and Bank Transactions

## Project Overview

This project aims to improve fraud detection for both e-commerce transactions and bank credit card transactions. The objective is to build machine learning models capable of identifying fraudulent activities while minimizing false positives and false negatives.

The project uses two datasets:

1. **Fraud_Data.csv** – E-commerce transaction data with user, device, and behavioral information.
2. **creditcard.csv** – Credit card transaction data with anonymized PCA-transformed features.

An additional dataset, **IpAddress_to_Country.csv**, is used to enrich the e-commerce data with geolocation information.

---

## Objectives

* Perform exploratory data analysis (EDA) on both datasets.
* Clean and preprocess the data.
* Enrich e-commerce transactions with country information using IP address mapping.
* Engineer fraud-related features.
* Handle class imbalance using SMOTE.
* Prepare datasets for machine learning modeling.
* Build and evaluate fraud detection models.
* Interpret model predictions and provide business recommendations.

---

## Data Preprocessing

### Fraud Dataset

* Removed duplicate records.
* Converted timestamp columns to datetime format.
* Mapped IP addresses to countries using IP range lookup.
* Created new features:

  * time_since_signup
  * hour_of_day
  * day_of_week
  * user_transaction_count
  * device_transaction_count
* One-hot encoded categorical variables.
* Scaled numerical features using StandardScaler.
* Applied SMOTE to address class imbalance.

### Credit Card Dataset

* Removed duplicate records.
* Scaled numerical features.
* Applied SMOTE on the training set to balance classes.

---

## Exploratory Data Analysis

EDA was performed separately for both datasets and included:

* Dataset overview
* Missing value analysis
* Duplicate analysis
* Univariate analysis
* Bivariate analysis
* Class imbalance analysis
* Correlation analysis
* Fraud pattern investigation

---

## Tools and Libraries

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Imbalanced-learn (SMOTE)

---

## Expected Outcome

The final outcome of this project is a robust fraud detection system capable of identifying fraudulent transactions in both e-commerce and banking environments while providing insights into the factors that contribute most to fraud.

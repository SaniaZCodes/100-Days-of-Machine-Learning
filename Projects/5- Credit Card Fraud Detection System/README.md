# 💳 Credit Card Fraud Detection System Using Machine Learning

## 📌 Overview

This project aims to detect fraudulent credit card transactions using Machine Learning and Ensemble Learning techniques.

The objective was to build a complete end-to-end Machine Learning pipeline, handle extreme class imbalance, compare multiple ensemble algorithms, optimize the best-performing model, and select the most effective model for fraud detection.

This project combines concepts from:

- Data Preprocessing
- Exploratory Data Analysis (EDA)
- Ensemble Learning
- Imbalanced Data Handling (SMOTE)
- Hyperparameter Optimization (Optuna)

---

# 🎯 Problem Statement

Predict whether a credit card transaction is:

- Legitimate Transaction (Class = 0)
- Fraudulent Transaction (Class = 1)

### Problem Type

- Binary Classification

---

# 📊 Dataset Information

### Dataset

**Credit Card Fraud Detection Dataset**

The dataset contains credit card transactions made by European cardholders.

### Dataset Characteristics

- 284,807 transactions
- 30 input features
- 1 target variable

### Features

- Time
- V1 – V28 (PCA-transformed features)
- Amount

### Target Variable

- 0 → Legitimate Transaction
- 1 → Fraudulent Transaction

### Important Observation

The dataset is highly imbalanced.

After duplicate removal:

- Legitimate Transactions ≈ 283,253
- Fraudulent Transactions ≈ 473

Fraud transactions represent only a tiny fraction of the dataset.

---

# 🔍 Exploratory Data Analysis (EDA)

The following analyses were performed:

- Missing Values Analysis
- Duplicate Values Analysis
- Target Variable Analysis
- Correlation Analysis
- Distribution Analysis
- Skewness Analysis
- Outlier Analysis
- Correlation Heatmap

---

## Key Findings

### Missing Values

✅ No Missing Values Found

---

### Duplicate Records

✅ 1,081 Duplicate Transactions Found

✅ Duplicate Records Removed

---

### Class Distribution

✅ Extremely Imbalanced Dataset

- Legitimate Transactions ≈ 99.8%
- Fraudulent Transactions ≈ 0.2%

---

### Correlation Analysis

✅ Most PCA features showed weak correlations with the target variable.

✅ V17, V14, and V12 showed the strongest relationships with fraud.

---

### Distribution Analysis

### Time

✅ Approximately Normally Distributed

### Amount

✅ Highly Right-Skewed

✅ Contains Extreme Values

---

### Skewness Analysis

### Time

```text
Skewness ≈ -0.04
```

Approximately symmetric.

### Amount

```text
Skewness ≈ 14+
```

Extremely positively skewed.

---

### Outlier Analysis

✅ Time did not exhibit a severe outlier problem.

✅ Amount contained a large number of extreme transaction values.

Because these values may represent real fraudulent transactions, no outlier removal was performed.

---

# ⚙️ Data Preprocessing

The following preprocessing steps were applied:

- Duplicate Removal
- Train–Test Split
- Yeo-Johnson Transformation
- Feature Scaling
- SMOTE

---

## Train-Test Split

Dataset was divided into:

- 80% Training Data
- 20% Testing Data

Stratified sampling was used to preserve class distribution.

---

## Yeo-Johnson Transformation

Applied on:

```text
Amount
```

Reason:

- Extreme positive skewness
- Highly non-normal distribution

Result:

✅ Amount distribution became nearly symmetric

---

## Feature Scaling

Technique Used:

```text
StandardScaler
```

Purpose:

- Standardize feature scales
- Prepare data for model training

---

# ⚖️ Handling Imbalanced Data

### Technique Used

✅ SMOTE (Synthetic Minority Oversampling Technique)

---

### Why SMOTE?

The dataset contained very few fraud observations.

SMOTE generated synthetic fraud samples and balanced the training dataset.

---

### Class Distribution

#### Before SMOTE

```text
Class 0 = 226,602

Class 1 = 378
```

#### After SMOTE

```text
Class 0 = 226,602

Class 1 = 226,602
```

Result:

✅ Perfectly Balanced Training Dataset

---

# 🤖 Models Implemented

The following Ensemble Learning models were trained and evaluated:

### Random Forest

Bagging-based ensemble model that combines multiple Decision Trees.

---

### AdaBoost

Boosting algorithm that focuses on misclassified observations.

---

### Gradient Boosting

Sequential boosting algorithm that learns residual errors.

---

### XGBoost

Optimized Gradient Boosting algorithm with regularization and enhanced performance.

---

### Stacking

Advanced ensemble technique that combines predictions from multiple models using a Meta Model.

---

# 📈 Model Performance

| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|---------|---------|---------|---------|---------|---------|
| Random Forest | 99.84% | 51.30% | 83.16% | 63.45% | 97.93% |
| AdaBoost | 96.77% | 4.27% | 85.26% | 8.12% | 96.19% |
| Gradient Boosting | 98.12% | 7.00% | 83.16% | 12.91% | 97.39% |
| XGBoost | 98.43% | 8.47% | 85.26% | 15.41% | 97.75% |
| Stacking | 99.38% | 18.38% | 78.95% | 29.82% | 95.59% |

---

# 🚀 Hyperparameter Optimization

### Technique Used

✅ Optuna

---

### Purpose

Automatically search for optimal Random Forest hyperparameters.

---

### Best Hyperparameters Found

```text
n_estimators = 234

max_depth = 18

min_samples_split = 17

min_samples_leaf = 6
```

---

# 🏆 Final Model

## Tuned Random Forest Classifier

After Optuna optimization, the final Random Forest model achieved:

### Final Results

- Accuracy: 99.93%
- Precision: 80.43%
- Recall: 77.89%
- F1 Score: 79.14%
- ROC-AUC: 98.05%

---

# ✅ Why Random Forest Was Selected

Although several Ensemble Learning models were evaluated, Random Forest achieved the strongest overall balance between:

- Precision
- Recall
- F1 Score
- ROC-AUC

For fraud detection systems, reducing false fraud alerts while still identifying fraudulent transactions is critical.

Random Forest provided the best trade-off and was therefore selected as the final deployment model.

---

# 📊 Evaluation Metrics Used

### Accuracy

Measures the percentage of correctly classified transactions.

---

### Precision

Measures how many transactions predicted as fraud were actually fraudulent.

---

### Recall

Measures how many actual fraud transactions were successfully detected.

---

### F1 Score

Balances Precision and Recall.

---

### ROC-AUC

Measures the model’s ability to distinguish between fraudulent and legitimate transactions.

---

# 📌 Key Learnings

- End-to-End Machine Learning Workflow
- Exploratory Data Analysis (EDA)
- Duplicate Detection and Removal
- Feature Transformation
- Standardization
- Imbalanced Data Handling
- SMOTE
- Random Forest
- AdaBoost
- Gradient Boosting
- XGBoost
- Stacking Ensembles
- Optuna Hyperparameter Optimization
- Precision, Recall, F1 Score & ROC-AUC
- Model Comparison and Selection

---

# 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- Imbalanced-Learn
- XGBoost
- Optuna
- Joblib

---

# 🎯 Conclusion

This project successfully implemented a complete fraud detection pipeline using Machine Learning and Ensemble Learning techniques.

After extensive preprocessing, handling class imbalance with SMOTE, evaluating multiple ensemble models, and optimizing the best-performing model using Optuna, a Tuned Random Forest Classifier was selected as the final model.

The final model achieved strong Precision, Recall, F1 Score, and ROC-AUC performance, making it an effective solution for detecting fraudulent credit card transactions while minimizing false alerts.

This project demonstrates the practical application of Data Preprocessing, Ensemble Learning, Imbalanced Data Handling, and Hyperparameter Optimization in a real-world Machine Learning problem.

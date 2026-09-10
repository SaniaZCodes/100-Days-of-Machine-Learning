# ❤️ Heart Disease Prediction Using Machine Learning

## 📌 Overview

This project aims to predict whether a patient has heart disease based on various medical attributes. The objective was to apply a complete Machine Learning classification workflow, compare multiple classification algorithms, and identify the best-performing model.

---

# 🎯 Problem Statement

Predict whether a patient has heart disease or not.

### Target Variable

- 0 → No Heart Disease
- 1 → Heart Disease

### Problem Type

- Binary Classification

---

# 📊 Dataset Information

- 303 Patient Records
- 13 Features
- 1 Target Variable

### Features

- Age
- Sex
- Chest Pain Type (cp)
- Resting Blood Pressure (trestbps)
- Cholesterol (chol)
- Fasting Blood Sugar (fbs)
- Rest ECG (restecg)
- Maximum Heart Rate Achieved (thalach)
- Exercise Induced Angina (exang)
- Oldpeak
- Slope
- CA
- Thal

---

# 🔍 Exploratory Data Analysis (EDA)

The following analyses were performed:

- Missing Value Analysis
- Duplicate Value Analysis
- Target Distribution Analysis
- Correlation Analysis
- Outlier Detection
- Skewness Analysis
- Distribution Analysis

### Key Findings

✅ No Missing Values

✅ No Duplicate Records

✅ Fairly Balanced Dataset

✅ Strong Predictive Features:
- Thal
- CA
- Exang
- Oldpeak
- Chest Pain Type

✅ No severe multicollinearity detected

---

# ⚙️ Data Preprocessing

The following preprocessing steps were applied:

- Feature & Target Separation
- Train-Test Split (80:20)
- Feature Scaling using StandardScaler

---

# 🤖 Models Implemented

### Logistic Regression

A probabilistic classification algorithm used as the baseline classification model.

### Gaussian Naive Bayes

A probabilistic classification algorithm that assumes features follow a Gaussian distribution.

---

# 📈 Model Performance

| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|---------|---------|---------|---------|---------|---------|
| Logistic Regression | 88.5% | 87.9% | 90.6% | 89.2% | 92.1% |
| Gaussian Naive Bayes | 85.2% | 89.7% | 81.2% | 85.2% | 91.7% |

---

# 🏆 Best Model

### Logistic Regression

Logistic Regression achieved the best overall performance on the dataset.

### Why Logistic Regression?

✅ Higher Accuracy

✅ Higher Recall

✅ Higher F1 Score

✅ Higher ROC-AUC

Although Gaussian Naive Bayes achieved slightly higher Precision, Logistic Regression identified a larger number of actual heart disease patients.

Since Recall is particularly important in healthcare applications, Logistic Regression was selected as the final model.

---

# 📊 Evaluation Metrics Used

### Accuracy
Measures the percentage of correctly classified patients.

### Precision
Measures how many predicted positive cases were actually positive.

### Recall
Measures how many actual heart disease patients were correctly identified by the model.

### F1 Score
Balances Precision and Recall into a single metric.

### ROC-AUC
Measures the model's ability to distinguish between patients with and without heart disease.

---

# 📌 Key Learnings

- Binary Classification Workflow
- Exploratory Data Analysis (EDA)
- Feature Scaling
- Logistic Regression
- Gaussian Naive Bayes
- Confusion Matrix
- Accuracy, Precision, Recall & F1 Score
- ROC-AUC Evaluation
- Model Comparison and Selection

---

# 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn

---

# 🎯 Conclusion

Two classification algorithms were trained and evaluated for heart disease prediction. Logistic Regression outperformed Gaussian Naive Bayes across most evaluation metrics and achieved the best balance between overall accuracy and disease detection capability.

The final Logistic Regression model achieved:

- Accuracy: 88.5%
- Recall: 90.6%
- F1 Score: 89.2%
- ROC-AUC: 92.1%

Based on these results, Logistic Regression was selected as the final model for predicting heart disease.

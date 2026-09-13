# 🩺 Diabetes Prediction Using Machine Learning

## 📌 Overview

This project aims to predict whether a patient has diabetes based on various medical attributes. The objective was to apply a complete Machine Learning classification workflow, perform extensive data preprocessing, compare multiple classification algorithms, and select the most suitable model for deployment.

---

# 🎯 Problem Statement

Predict whether a patient has diabetes or not.

### Target Variable

- 0 → Non-Diabetic
- 1 → Diabetic

### Problem Type

- Binary Classification

---

# 📊 Dataset Information

- 768 Patient Records
- 8 Features
- 1 Target Variable

### Features

- Pregnancies
- Glucose
- BloodPressure
- SkinThickness
- Insulin
- BMI
- DiabetesPedigreeFunction
- Age

---

# 🔍 Exploratory Data Analysis (EDA)

The following analyses were performed:

- Missing Value Analysis
- Duplicate Value Analysis
- Target Distribution Analysis
- Correlation Analysis
- Distribution Analysis
- Skewness Analysis
- Outlier Detection

### Key Findings

✅ No Duplicate Records

✅ Hidden Missing Values Found

- Glucose = 0
- BloodPressure = 0
- SkinThickness = 0
- Insulin = 0
- BMI = 0

These values were treated as missing values.

✅ Moderately Imbalanced Dataset

- Non-Diabetic = 500
- Diabetic = 268

✅ Strongest Predictive Feature

- Glucose

✅ Highly Skewed Features

- Insulin
- DiabetesPedigreeFunction
- Age

✅ Outliers Detected

- Pregnancies
- Insulin
- BMI
- Age
- DiabetesPedigreeFunction

✅ Outliers were retained because they represented realistic medical observations.

---

# ⚙️ Data Preprocessing

The following preprocessing steps were applied:

- Feature & Target Separation
- Train-Test Split (80:20)
- Hidden Missing Value Treatment
- Median Imputation
- KNN Imputation
- Outlier Analysis
- Yeo-Johnson Transformation
- Feature Scaling using StandardScaler

### Missing Value Handling

#### Median Imputation

Applied on:

- Glucose
- BloodPressure
- BMI

#### KNN Imputation

Applied on:

- SkinThickness
- Insulin

### Data Transformation

Yeo-Johnson Transformation was applied to reduce skewness and make feature distributions closer to normal.

### Feature Engineering

Skipped because the dataset already contains meaningful medical features and no useful domain-based features could be created.

### Encoding

Skipped because all features were numerical.

### PCA

Skipped because the dataset contains only 8 features and dimensionality reduction was not required.

---

# 🤖 Models Implemented

### Logistic Regression

A linear classification algorithm used as a strong baseline model.

### Gaussian Naive Bayes

A probabilistic classification algorithm based on Bayes' Theorem.

### K-Nearest Neighbors (KNN)

A distance-based classification algorithm that classifies data based on neighboring samples.

### Support Vector Machine (SVM)

A powerful classification algorithm that finds the optimal decision boundary between classes.

### Decision Tree

A tree-based algorithm that makes predictions using a series of decision rules.

---

# 📈 Model Performance

| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|---------|---------|---------|---------|---------|---------|
| Logistic Regression | 75.3% | 65.5% | 65.5% | 65.5% | 82.1% |
| Gaussian Naive Bayes | 74.7% | 62.5% | 72.7% | 67.2% | 81.9% |
| SVM | 72.7% | 61.4% | 63.6% | 62.5% | 81.2% |
| KNN | 74.0% | 61.9% | 70.9% | 66.1% | 78.2% |
| Decision Tree | 66.9% | 53.3% | 58.2% | 55.7% | 64.9% |

---

# 🏆 Best Model

## Gaussian Naive Bayes

Gaussian Naive Bayes was selected as the final model for deployment.

### Why Gaussian Naive Bayes?

✅ Highest Recall

✅ Highest F1 Score

✅ Competitive Accuracy

✅ Competitive ROC-AUC Score

Although Logistic Regression achieved slightly higher Accuracy and ROC-AUC, the difference was relatively small.

Gaussian Naive Bayes achieved significantly better Recall, meaning it successfully identified more diabetic patients.

Since missing a diabetic patient can be more critical than incorrectly classifying a healthy patient, Recall was given higher importance during model selection.

---

# 📊 Evaluation Metrics Used

### Accuracy

Measures the percentage of correctly classified patients.

### Precision

Measures how many predicted diabetic patients were actually diabetic.

### Recall

Measures how many actual diabetic patients were correctly identified by the model.

### F1 Score

Balances Precision and Recall into a single metric.

### ROC-AUC

Measures the model's ability to distinguish between diabetic and non-diabetic patients.

---

# 📌 Key Learnings

- End-to-End Machine Learning Workflow
- Exploratory Data Analysis (EDA)
- Missing Value Handling
- KNN Imputation
- Yeo-Johnson Transformation
- Feature Scaling
- Logistic Regression
- Gaussian Naive Bayes
- KNN Classification
- Support Vector Machine (SVM)
- Decision Tree Classification
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

Five classification algorithms were trained and evaluated for diabetes prediction.

Gaussian Naive Bayes achieved the highest Recall (72.7%) and highest F1 Score (67.2%), making it the most effective model for identifying diabetic patients.

The final Gaussian Naive Bayes model achieved:

- Accuracy: 74.7%
- Recall: 72.7%
- F1 Score: 67.2%
- ROC-AUC: 81.9%

Based on these results, Gaussian Naive Bayes was selected as the final model for diabetes prediction because correctly identifying diabetic patients was prioritized over a small increase in overall accuracy.

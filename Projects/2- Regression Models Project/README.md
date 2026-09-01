# 🏠 House Price Prediction Using Regression Models

## 📌 Project Overview

This project focuses on predicting house prices using different Regression Algorithms and comparing their performance.

The primary goal was to understand how different regression models behave on a real-world dataset and determine which model provides the best balance between accuracy and generalization.

This project is part of my Machine Learning learning journey and serves as the practical implementation of the Regression phase.

---

# 🎯 Objectives

- Predict house prices using machine learning models.
- Compare different regression techniques.
- Analyze model performance using evaluation metrics.
- Understand model generalization through training and testing scores.
- Explore regularization techniques such as Ridge, Lasso, and Elastic Net.

---

# 📊 Dataset

The project uses a House Price Prediction dataset containing various housing-related features.

Target Variable:

```text
SalePrice
```

The objective is to predict the selling price of a house based on its characteristics.

---

# ⚙️ Data Preprocessing

The dataset was preprocessed in a separate preprocessing project before applying Regression models.

The preprocessing pipeline included:

## ✅ Exploratory Data Analysis (EDA)

- Univariate Analysis
- Bivariate Analysis
- Multivariate Analysis
- Histograms
- Boxplots
- Skewness Analysis

## ✅ Missing Value Handling

- Complete Case Analysis
- Mean Imputation
- Median Imputation
- Random Sample Imputation
- Missing Indicator
- KNN Imputer
- MICE (Iterative Imputer)

## ✅ Feature Engineering

### Scaling

- Standardization (Z-Score Scaling)
- Min-Max Scaling
- MaxAbs Scaling
- Robust Scaling

### Encoding

- Ordinal Encoding
- One-Hot Encoding

### Transformations

- Log Transformation
- Reciprocal Transformation
- Square Root Transformation
- Box-Cox Transformation
- Yeo-Johnson Transformation

## ✅ Additional Techniques

- Function Transformer
- Column Transformer
- Pipeline
- Feature Construction
- Feature Splitting
- Date-Time Feature Extraction

## ✅ Outlier Handling

- Z-Score Method
- IQR Method
- Percentile Method
- Winsorization

## ✅ Dimensionality Reduction

- Curse of Dimensionality
- Principal Component Analysis (PCA)
- Eigenvalues & Eigenvectors
- Explained Variance Ratio

---

# 🤖 Machine Learning Models

The following regression models were trained and evaluated:

## 1️⃣ Multiple Linear Regression

Used as the baseline model.

Since PCA generated multiple principal components, the model effectively becomes Multiple Linear Regression rather than Simple Linear Regression.

---

## 2️⃣ Ridge Regression

Uses L2 Regularization.

Purpose:

```text
Reduce overfitting by shrinking coefficient values.
```

---

## 3️⃣ Lasso Regression

Uses L1 Regularization.

Purpose:

```text
Reduce overfitting and perform feature selection.
```

---

## 4️⃣ Elastic Net Regression

Combines:

```text
L1 + L2 Regularization
```

Purpose:

```text
Combine the strengths of Ridge and Lasso.
```

---

# 📈 Evaluation Metrics

The models were evaluated using:

## R² Score

Measures how much variance in the target variable is explained by the model.

Higher is better.

---

## Adjusted R² Score

An improved version of R² that considers the number of features used in the model.

---

## MAE (Mean Absolute Error)

Measures the average absolute prediction error.

Lower is better.

---

## MSE (Mean Squared Error)

Measures the average squared prediction error.

Lower is better.

---

## RMSE (Root Mean Squared Error)

Measures prediction error in the original target unit.

Lower is better.

---

# 📊 Model Comparison

| Model | Train R² | Test R² |
|---------|---------|---------|
| Linear Regression | 0.8838 | 0.8518 |
| Ridge Regression | 0.8838 | 0.8518 |
| Lasso Regression | 0.8838 | 0.8518 |
| Elastic Net Regression | 0.8726 | 0.8431 |

---

# 🔍 Results Analysis

### Linear Regression

- Strong Training Performance
- Strong Test Performance
- No significant signs of overfitting

### Ridge Regression

- Produced results almost identical to Linear Regression
- Regularization had minimal impact

### Lasso Regression

- Produced similar performance to Linear Regression
- Feature selection benefits were limited due to the use of PCA

### Elastic Net Regression

- Slightly lower Train and Test R² scores
- Did not outperform the baseline model

---

# 🎯 Key Findings

✅ The model showed no significant underfitting.

✅ The model showed no significant overfitting.

✅ Train and Test scores remained very close.

✅ Proper preprocessing greatly improved model performance.

✅ PCA helped reduce dimensionality while retaining important information.

✅ Regularized models did not significantly outperform the baseline model.

✅ Linear Regression provided the best balance of simplicity and performance.

---

# 🏆 Best Model

```text
Multiple Linear Regression
```

### Why?

- Highest Test R² Score
- Strong generalization
- No noticeable overfitting
- Simpler than regularized alternatives

---

# 📚 Key Learnings

Through this project, I learned:

- How Linear Regression works in real-world datasets.
- How to evaluate regression models using multiple metrics.
- The difference between underfitting and overfitting.
- When to use Polynomial Regression, Ridge Regression, Lasso Regression, and Elastic Net Regression.
- The importance of proper preprocessing and dimensionality reduction.
- That more complex models do not always outperform simpler models.

---

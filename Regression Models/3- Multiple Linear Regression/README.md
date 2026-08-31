# Multiple Linear Regression

## What is Multiple Linear Regression?

Multiple Linear Regression is a supervised machine learning algorithm used to predict a continuous numerical value using multiple independent variables (features).

It is an extension of Simple Linear Regression.

### Examples

- House Price Prediction
- Salary Prediction
- Sales Prediction
- Demand Forecasting

---

# Why Do We Use It?

In real-world problems, the target variable usually depends on multiple factors.

For example, house price depends on:

- Area
- Bedrooms
- Bathrooms
- Garage
- Location

Instead of using only one feature, Multiple Linear Regression uses all relevant features together to make predictions.

---

# Difference Between Simple and Multiple Linear Regression

## Simple Linear Regression

Uses only one input feature.

Example:

```text
Area → House Price
```

Equation:

```text
Y = mX + c
```

---

## Multiple Linear Regression

Uses multiple input features.

Example:

```text
Area + Bedrooms + Garage → House Price
```

Equation:

```text
Y = m₁X₁ + m₂X₂ + m₃X₃ + ... + c
```

---

# Mathematical Equation

```text
Y = m₁X₁ + m₂X₂ + m₃X₃ + ... + c
```

Where:

- Y = Target Variable
- X₁, X₂, X₃ = Features
- m₁, m₂, m₃ = Coefficients
- c = Intercept

---

# What Are Coefficients?

Coefficients represent the contribution or importance of each feature.

Example:

```text
Price =
100 × Area
+
5000 × Bedrooms
+
10000 × Garage
+
20000
```

Here:

```text
Area Coefficient = 100
Bedroom Coefficient = 5000
Garage Coefficient = 10000
```

---

# Meaning of a Coefficient

Suppose:

```text
Area Coefficient = 100
```

This means:

> If area increases by 1 unit, house price increases by 100 units while keeping all other features constant.

---

# What Does "Keeping Other Features Constant" Mean?

Suppose two houses:

### House A

```text
Area = 1000
Bedrooms = 2
```

### House B

```text
Area = 1001
Bedrooms = 2
```

Only area changed.

Bedrooms remained fixed.

If price increases by 100 units, then:

```text
Area Coefficient = 100
```

This is called measuring the effect of a feature while keeping all other features constant.

---

# What is Intercept?

Intercept is the predicted value when all feature values become zero.

Example:

```text
Price =
100 × Area
+
5000 × Bedrooms
+
10000
```

When:

```text
Area = 0
Bedrooms = 0
```

Predicted Price:

```text
10000
```

Therefore:

```text
Intercept = 10000
```

---

# Goal of Multiple Linear Regression

The goal is to find:

```text
Best Coefficients
+
Best Intercept
```

such that prediction error becomes minimum.

---

# Input / Output

## Input

Multiple independent variables.

Example:

```text
Area
Bedrooms
Bathrooms
Garage
```

---

## Output

One numerical prediction.

Example:

```text
House Price
```

---

# When to Use Multiple Linear Regression?

✅ Multiple input features

✅ Numerical target variable

✅ Relationship is approximately linear

✅ Need interpretable predictions

Examples:

- House Price Prediction
- Salary Prediction
- Sales Forecasting

---

# When Not to Use Multiple Linear Regression?

❌ Classification problems

❌ Highly non-linear relationships

❌ Image classification

❌ Complex pattern recognition

Examples:

- Spam Detection
- Cat vs Dog Classification
- Face Recognition

---

# Advantages

✅ Easy to understand

✅ Easy to implement

✅ Fast training

✅ Uses multiple features

✅ Interpretable coefficients

✅ Good baseline model

---

# Disadvantages

❌ Sensitive to outliers

❌ Assumes linear relationship

❌ Struggles with complex non-linear patterns

❌ Can suffer from multicollinearity

---

# Assumptions

1. Linear relationship between features and target.

2. No high multicollinearity.

3. Independent observations.

4. Constant variance of errors.

5. Errors should be approximately normally distributed.

6. No significant outliers.

---

# What Does a Positive Coefficient Mean?

Example:

```text
Bedroom Coefficient = +5000
```

Meaning:

> Increasing bedrooms increases house price.

---

# What Does a Negative Coefficient Mean?

Example:

```text
HouseAge Coefficient = -200
```

Meaning:

> As house age increases, house price decreases.

---

# sklearn Implementation

```python
from sklearn.linear_model import LinearRegression

# Create Model
model = LinearRegression()

# Train Model
model.fit(X_train, y_train)

# Predictions
y_pred = model.predict(X_test)
```

---

# Accessing Coefficients

```python
print(model.coef_)
```

Output:

```text
[100, 5000, 10000]
```

Each value represents the coefficient of a feature.

---

# Accessing Intercept

```python
print(model.intercept_)
```

Output:

```text
20000
```

---

# Model Evaluation

Common evaluation metrics:

## MAE

Mean Absolute Error

---

## MSE

Mean Squared Error

---

## RMSE

Root Mean Squared Error

---

## R² Score

Measures how much variance is explained by the model.

---

## Adjusted R²

Used when working with multiple features.

Penalizes unnecessary features.

---

# Evaluation Code

```python
from sklearn.metrics import (
    mean_absolute_error,
    mean_squared_error,
    r2_score
)

mae = mean_absolute_error(y_test, y_pred)

mse = mean_squared_error(y_test, y_pred)

rmse = mean_squared_error(
    y_test,
    y_pred,
    squared=False
)

r2 = r2_score(y_test, y_pred)

print("MAE:", mae)
print("MSE:", mse)
print("RMSE:", rmse)
print("R²:", r2)
```

---

# Real World Use Cases

- House Price Prediction
- Salary Prediction
- Revenue Forecasting
- Demand Forecasting
- Sales Prediction
- Business Analytics

---

# Interview Questions

## Q1. What is Multiple Linear Regression?

Multiple Linear Regression is a supervised learning algorithm that predicts a numerical value using multiple independent variables.

---

## Q2. Difference Between Simple and Multiple Linear Regression?

### Simple Linear Regression

Uses one input feature.

### Multiple Linear Regression

Uses multiple input features.

---

## Q3. What does a coefficient represent?

A coefficient represents the importance or contribution of a feature toward predicting the target variable.

---

## Q4. Why do we need multiple coefficients?

Because each feature influences the target variable differently.

---

## Q5. What does a positive coefficient indicate?

A positive coefficient indicates that increasing the feature increases the target variable.

---

## Q6. What does a negative coefficient indicate?

A negative coefficient indicates that increasing the feature decreases the target variable.

---

## Q7. What is the role of the intercept?

The intercept is the predicted value when all feature values are zero.

---

## Q8. What is meant by "keeping all other features constant"?

It means measuring the effect of one feature while keeping the remaining features unchanged.

---

## Q9. What is the goal of Multiple Linear Regression?

To find the best coefficients and intercept that minimize prediction error.

---

## Q10. Give a real-world example of Multiple Linear Regression.

Predicting house price using:

```text
Area
Bedrooms
Bathrooms
Garage
Location
```

---

# Revision Notes

```text
Multiple Linear Regression
↓
Multiple Input Features

Equation
↓
Y = m₁X₁ + m₂X₂ + ... + c

X₁, X₂, X₃
↓
Features

m₁, m₂, m₃
↓
Coefficients

Coefficient
↓
Importance of Feature

Positive Coefficient
↓
Target Increases

Negative Coefficient
↓
Target Decreases

Goal
↓
Find Best Coefficients

Output
↓
Numerical Prediction
```

---

# Summary

Multiple Linear Regression is an extension of Simple Linear Regression that uses multiple independent variables to predict a numerical target variable.

The model learns coefficients for each feature and an intercept, then combines them to make predictions while minimizing prediction error.

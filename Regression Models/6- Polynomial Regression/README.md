# Polynomial Regression

## What is Polynomial Regression?

Polynomial Regression is a regression technique used to model non-linear relationships between independent variables and the target variable.

It extends Linear Regression by creating additional polynomial features such as:

```text
X²
X³
X⁴
```

and then applying Linear Regression on those transformed features.

---

# Why Do We Need Polynomial Regression?

Linear Regression assumes a straight-line relationship between the input and output.

Example:

```text
Experience ↑
Salary ↑
```

This works well when the relationship is linear.

However, many real-world relationships are non-linear.

Examples:

- Car Age vs Car Price
- Advertising Budget vs Sales
- Temperature vs Electricity Consumption
- Study Hours vs Marks

In such situations, a straight line may not fit the data properly.

Polynomial Regression helps capture these curved relationships.

---

# Linear Regression vs Polynomial Regression

## Linear Regression

Equation:

```text
Y = mX + c
```

Produces:

```text
Straight Line
```

---

## Polynomial Regression

Equation:

```text
Y = a + bX + cX²
```

or

```text
Y = a + bX + cX² + dX³
```

Produces:

```text
Curve
```

---

# Is Polynomial Regression a Separate Algorithm?

No.

This is one of the most important interview concepts.

Polynomial Regression is:

```text
Polynomial Feature Engineering
+
Linear Regression
```

The model is still:

```python
LinearRegression()
```

Only the features change.

---

# How Polynomial Regression Works

## Step 1

Start with original feature:

```text
X
```

---

## Step 2

Create new polynomial features:

```text
X²

X³

X⁴
```

---

## Step 3

Train Linear Regression using the transformed features.

---

## Step 4

Model learns a curved relationship.

---

# Feature Transformation Example

Original Dataset:

| X |
|---|
|1|
|2|
|3|
|4|

---

## Degree = 2

Transformed Dataset:

| X | X² |
|---|---|
|1|1|
|2|4|
|3|9|
|4|16|

---

## Degree = 3

Transformed Dataset:

| X | X² | X³ |
|---|---|---|
|1|1|1|
|2|4|8|
|3|9|27|
|4|16|64|

---

# Mathematical Equation

## Degree 2

```text
Y = a + bX + cX²
```

---

## Degree 3

```text
Y = a + bX + cX² + dX³
```

---

Where:

```text
a = Intercept

b = Coefficient of X

c = Coefficient of X²

d = Coefficient of X³
```

---

# What is Degree?

Degree determines the highest power of the feature in the model.

---

## Degree 1

```text
X
```

Equivalent to:

```text
Simple Linear Regression
```

---

## Degree 2

```text
X²
```

Creates a quadratic curve.

---

## Degree 3

```text
X³
```

Creates a more flexible curve.

---

## Higher Degree

```text
X⁴
X⁵
X⁶
```

Creates increasingly complex curves.

---

# Input / Output

## Input

One or more numerical features.

Example:

```text
Experience

Car Age

Advertisement Budget
```

---

## Output

Continuous numerical value.

Example:

```text
Salary

Car Price

Sales
```

---

# When to Use Polynomial Regression?

✅ Relationship is non-linear

✅ Linear Regression performs poorly

✅ Numerical target variable

✅ Data follows a curved pattern

Examples:

- Car Price Prediction
- Sales Forecasting
- Demand Prediction
- Growth Analysis

---

# When Not to Use Polynomial Regression?

❌ Classification problems

❌ Extremely high-dimensional data

❌ Highly complex datasets requiring advanced models

❌ Very high polynomial degrees

---

# Advantages

✅ Captures non-linear relationships

✅ Easy to implement

✅ More flexible than Linear Regression

✅ Works well for moderately curved datasets

✅ Still uses Linear Regression internally

---

# Disadvantages

❌ Can overfit easily

❌ High-degree polynomials become unstable

❌ Harder to interpret

❌ Sensitive to outliers

---

# Assumptions

1. Relationship can be approximated using a polynomial function.

2. Observations are independent.

3. Residuals should have constant variance.

4. Residuals should be approximately normally distributed.

5. No severe multicollinearity among generated features.

---

# Overfitting in Polynomial Regression

One of the biggest risks is overfitting.

Example:

```text
Degree = 20
```

The model may memorize training data instead of learning the true pattern.

Result:

✅ Excellent Training Performance

❌ Poor Testing Performance

---

# Underfitting in Polynomial Regression

Example:

```text
Degree = 1
```

If the actual relationship is curved:

```text
Straight Line
```

will fail to capture the pattern.

Result:

❌ Poor Training Performance

❌ Poor Testing Performance

---

# sklearn Implementation

## Step 1: Import Libraries

```python
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression
```

---

## Step 2: Create Polynomial Features

```python
poly = PolynomialFeatures(degree=2)
```

Explanation:

```text
Create X² features.
```

---

## Step 3: Transform Training Data

```python
X_train_poly = poly.fit_transform(X_train)
```

Example:

Original:

```text
2
```

Becomes:

```text
[1, 2, 4]
```

Representing:

```text
1
X
X²
```

---

## Step 4: Transform Test Data

```python
X_test_poly = poly.transform(X_test)
```

Transforms test data using the same mapping.

---

## Step 5: Create Model

```python
model = LinearRegression()
```

Creates a Linear Regression model.

---

## Step 6: Train Model

```python
model.fit(X_train_poly, y_train)
```

Learns coefficients and intercept.

---

## Step 7: Make Predictions

```python
y_pred = model.predict(X_test_poly)
```

Generates predictions.

---

# Complete sklearn Code

```python
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression

poly = PolynomialFeatures(degree=2)

X_train_poly = poly.fit_transform(X_train)
X_test_poly = poly.transform(X_test)

model = LinearRegression()

model.fit(X_train_poly, y_train)

y_pred = model.predict(X_test_poly)
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

Measures explained variance.

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

- Car Price Prediction
- Sales Forecasting
- Population Growth Analysis
- Demand Forecasting
- Revenue Prediction
- Business Growth Modeling

---

# Interview Questions

## Q1. What is Polynomial Regression?

Polynomial Regression is a regression technique used to model non-linear relationships by creating polynomial features and then applying Linear Regression.

---

## Q2. Is Polynomial Regression a separate machine learning algorithm?

No.

It is Linear Regression applied to polynomially transformed features.

---

## Q3. Why do we use Polynomial Regression?

To capture non-linear relationships that cannot be modeled using a straight line.

---

## Q4. What is the role of degree in Polynomial Regression?

Degree determines the highest power of the feature used for modeling.

---

## Q5. What happens when the degree is very high?

The model may overfit the training data.

---

## Q6. What is Degree 1 equivalent to?

Degree 1 is equivalent to Linear Regression.

---

## Q7. Why do we create X² and X³ features?

To allow the model to learn curved relationships.

---

## Q8. What is the biggest disadvantage of Polynomial Regression?

Overfitting.

---

## Q9. Does Polynomial Regression use Linear Regression internally?

Yes.

Polynomial features are created first, and then Linear Regression is applied.

---

## Q10. Give a real-world use case of Polynomial Regression.

Predicting car prices using vehicle age where the relationship is non-linear.

---

# Revision Notes

```text
Linear Regression
↓
Straight Line

Polynomial Regression
↓
Curve

Model Used
↓
Linear Regression

How?
↓
Create X², X³, X⁴ Features

Degree
↓
Highest Power

Degree 1
↓
Linear Regression

Degree 2+
↓
Polynomial Regression

Risk
↓
Overfitting

Advantage
↓
Captures Non-Linear Relationships
```

---

# Summary

Polynomial Regression is used when the relationship between features and the target variable is non-linear.

It is not a separate machine learning algorithm. Instead, it creates polynomial features such as X², X³, and X⁴ and then applies Linear Regression to those transformed features.

It is powerful for modeling curved relationships but must be used carefully because higher polynomial degrees can lead to overfitting.

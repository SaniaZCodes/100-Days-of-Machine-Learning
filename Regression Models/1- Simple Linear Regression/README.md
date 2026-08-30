# Simple Linear Regression

## What is Simple Linear Regression?

Simple Linear Regression is a supervised machine learning algorithm used to predict a continuous numerical value using a single independent variable.

Examples:

- Experience → Salary
- Study Hours → Marks
- House Area → House Price

---

## Why Do We Use It?

Simple Linear Regression is used to find the relationship between one input feature and one output variable and use that relationship for prediction.

---

## Mathematical Equation

```text
Y = mX + c
```

Where:

- Y = Dependent Variable (Target)
- X = Independent Variable (Feature)
- m = Slope
- c = Intercept

---

## What is Slope?

Slope represents how much Y changes when X increases by 1 unit.

Example:

```text
Salary = 5000 × Experience + 10000
```

Here:

- Slope = 5000

Meaning:

- Every additional year of experience increases salary by 5000.

---

## What is Intercept?

Intercept represents the value of Y when X = 0.

Example:

```text
Salary = 5000 × Experience + 10000
```

When:

```text
Experience = 0
```

Salary:

```text
10000
```

Therefore:

- Intercept = 10000

---

## When to Use It?

✅ Only one input feature

✅ Numerical target variable

✅ Linear relationship between input and output

Examples:

- Hours Studied → Marks
- Area → House Price
- Experience → Salary

---

## When Not to Use It?

❌ Multiple input features

❌ Non-linear relationships

❌ Classification problems

Examples:

- Spam Detection
- Disease Classification
- Pass / Fail Prediction

---

## Advantages

- Easy to understand
- Fast training
- Easy implementation
- Highly interpretable
- Good baseline model

---

## Disadvantages

- Assumes linear relationship
- Sensitive to outliers
- Cannot capture complex patterns
- Limited flexibility

---

## Assumptions

1. Linear relationship between X and Y
2. Independent observations
3. Constant variance of errors
4. Normally distributed errors
5. No significant outliers

---

## sklearn Implementation

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()

model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

---

## Evaluation Metrics

Common evaluation metrics:

- MAE
- MSE
- RMSE
- R² Score

---

## Interview Questions

### Q1. What is Simple Linear Regression?

Simple Linear Regression is a supervised learning algorithm that models the relationship between one independent variable and one dependent variable using a straight line.

---

### Q2. Why is it called "Simple"?

Because it uses only one independent variable for prediction.

---

### Q3. What is the equation of Simple Linear Regression?

```text
Y = mX + c
```

---

### Q4. What is Slope?

Slope represents the change in Y for a one-unit increase in X.

---

### Q5. What is Intercept?

Intercept is the predicted value of Y when X = 0.

---

### Q6. What is a Best Fit Line?

A best fit line is the line that minimizes prediction error and stays closest to all data points.

---

## 1-Minute Revision

```text
Regression
↓
Predict Numerical Values

Simple Linear Regression
↓
One Input Feature

Y = mX + c

m = Slope

c = Intercept

Goal:
Find Best Fit Line

Minimize Error
```

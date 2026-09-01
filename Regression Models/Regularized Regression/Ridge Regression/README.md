# Ridge Regression

## Overview

Ridge Regression is a regularized version of Linear Regression used to reduce overfitting.

It adds a penalty term to the cost function and shrinks large coefficient values.

---

# Why Do We Need Ridge Regression?

Linear Regression may overfit the training data.

Example:

```text
Train R² = 0.99

Test R² = 0.70
```

This means:

```text
Training Performance = Excellent

Testing Performance = Poor
```

The model memorized the training data.

This problem is called:

```text
Overfitting
```

---

# Solution

```text
Ridge Regression
```

Ridge controls coefficient values and reduces model complexity.

---

# What is Regularization?

Regularization is a technique used to reduce overfitting by controlling model complexity.

---

# What is Ridge Regression?

Ridge Regression is Linear Regression with an added penalty term.

---

# Linear Regression Cost Function

```text
Cost = MSE
```

---

# Ridge Regression Cost Function

```text
Cost = MSE + λΣ(m²)
```

---

# Formula Explanation

## MSE

Prediction Error.

---

## λ (Lambda)

Regularization Strength.

Controls the amount of penalty.

---

## m²

Squared coefficient values.

Large coefficients receive larger penalties.

---

# What Does Ridge Do?

Before Ridge:

```text
Area      = 50000

Bedrooms  = 30000

Garage    = 10000
```

After Ridge:

```text
Area      = 500

Bedrooms  = 300

Garage    = 100
```

Coefficients become smaller.

---

# Important Point

Ridge:

```text
Shrinks Features ✅
```

Ridge:

```text
Removes Features ❌
```

All features remain in the model.

---

# Lambda (λ)

Controls the strength of regularization.

---

## Lambda = 0

```text
Linear Regression
```

---

## Small Lambda

```text
Small Penalty
```

---

## Large Lambda

```text
Strong Penalty
```

---

## Very Large Lambda

```text
Underfitting Risk
```

---

# Ridge Uses L2 Regularization

Ridge applies:

```text
L2 Regularization
```

Penalty:

```text
Σ(m²)
```

Easy Memory:

```text
Ridge
↓
L2
↓
Square
```

---

# Advantages

✅ Reduces Overfitting

✅ Handles Multicollinearity

✅ Improves Generalization

✅ Keeps All Features

✅ Stable Model

---

# Disadvantages

❌ Does Not Remove Features

❌ Lambda Selection Required

❌ Very Large Lambda Can Cause Underfitting

---

# When To Use Ridge?

Use Ridge when:

✅ Model is overfitting

✅ Many features are present

✅ Multicollinearity exists

✅ Train score is much higher than test score

---

# Ridge vs Linear Regression

Linear Regression:

```text
Minimize Error
```

---

Ridge Regression:

```text
Minimize Error

+

Penalty
```

---

# Ridge vs Polynomial Regression

Polynomial Regression:

```text
Used For Underfitting
```

---

Ridge Regression:

```text
Used For Overfitting
```

---

# sklearn Code

```python
from sklearn.linear_model import Ridge

ridge = Ridge(alpha=1.0)

ridge.fit(X_train, y_train)

y_pred = ridge.predict(X_test)
```

---

# Ridge Using SGD

```python
from sklearn.linear_model import SGDRegressor

ridge_sgd = SGDRegressor(
    penalty='l2',
    alpha=0.0001,
    learning_rate='constant',
    eta0=0.01,
    max_iter=1000,
    random_state=42
)

ridge_sgd.fit(X_train, y_train)

y_pred = ridge_sgd.predict(X_test)
```

---

# Interview Questions

## What is Ridge Regression?

Ridge Regression is a regularized version of Linear Regression that reduces overfitting by shrinking coefficient values.

---

## What is Regularization?

A technique used to reduce overfitting by controlling model complexity.

---

## What is Lambda?

Regularization strength.

---

## What happens when Lambda = 0?

Ridge becomes Linear Regression.

---

## Does Ridge remove features?

No.

It only shrinks coefficients.

---

## Which regularization does Ridge use?

L2 Regularization.

---

# Revision Notes

```text
Ridge Regression
↓
Linear Regression + Penalty

Penalty
↓
L2 Regularization

Purpose
↓
Reduce Overfitting

Lambda
↓
Penalty Strength

Lambda = 0
↓
Linear Regression

Effect
↓
Smaller Coefficients

Remove Features?
↓
No
```
---

# Complete Workflow Code for Revision
## Step 1: Train-Test Split

```text
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

## Step 2: Linear Regression (Baseline)

```text
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score

lr = LinearRegression()

lr.fit(X_train, y_train)

y_train_pred = lr.predict(X_train)
y_test_pred = lr.predict(X_test)

train_r2 = r2_score(y_train, y_train_pred)
test_r2 = r2_score(y_test, y_test_pred)

print("Linear Regression")
print("Train R²:", train_r2)
print("Test R² :", test_r2)
```


## Step 3: Detect Underfitting / Overfitting


## Step 4: Polynomial Regression

```text
from sklearn.preprocessing import PolynomialFeatures
from sklearn.linear_model import LinearRegression

poly = PolynomialFeatures(degree=2)

X_train_poly = poly.fit_transform(X_train)
X_test_poly = poly.transform(X_test)

poly_model = LinearRegression()

poly_model.fit(X_train_poly, y_train)

train_r2 = poly_model.score(X_train_poly, y_train)
test_r2 = poly_model.score(X_test_poly, y_test)

print("Polynomial Regression")
print("Train R²:", train_r2)
print("Test R² :", test_r2)
```


## Step 5: Ridge Regression

```text
from sklearn.linear_model import Ridge

ridge = Ridge(alpha=1.0)

ridge.fit(X_train, y_train)

train_r2 = ridge.score(X_train, y_train)
test_r2 = ridge.score(X_test, y_test)

print("Ridge Regression")
print("Train R²:", train_r2)
print("Test R² :", test_r2)
```


## Step 6: Ridge Using SGD

```text
from sklearn.linear_model import SGDRegressor

ridge_sgd = SGDRegressor(
    penalty='l2',          # Ridge
    alpha=0.0001,
    max_iter=1000,
    learning_rate='constant',
    eta0=0.01,
    random_state=42
)

ridge_sgd.fit(X_train, y_train)

train_r2 = ridge_sgd.score(X_train, y_train)
test_r2 = ridge_sgd.score(X_test, y_test)

print("Ridge + SGD")
print("Train R²:", train_r2)
print("Test R² :", test_r2)
```


---

Preprocessing
↓
Linear Regression
↓
Check Train/Test Score

--------------------------------

Train Low + Test Low
↓
Underfitting
↓
Polynomial Regression

--------------------------------

Train High + Test Much Lower
↓
Overfitting
↓
Ridge Regression

--------------------------------

Need Ridge with GD
↓
SGDRegressor(penalty='l2')

--------------------------------

Ridge
↓
Shrink Features

Lasso
↓
Remove Features

Elastic Net
↓
Shrink + Remove Features

# Elastic Net Regression

# Overview

Elastic Net Regression is a regularized version of Linear Regression that combines:

```text
Lasso Regression (L1)

+

Ridge Regression (L2)
```

It is designed to reduce overfitting while also performing feature selection.

---

# Why Do We Need Elastic Net?

Suppose Linear Regression is overfitting.

Example:

```text
Train R² = 0.99

Test R² = 0.72
```

This indicates:

```text
Overfitting
```

We need regularization.

---

# Problem With Using Only Ridge

Ridge Regression:

✅ Reduces Overfitting

✅ Shrinks Coefficients

❌ Does Not Remove Features

---

Example:

Before:

```text
Area = 5000

Bedrooms = 3000

Garage = 1000
```

After Ridge:

```text
Area = 500

Bedrooms = 300

Garage = 100
```

All features remain.

---

# Problem With Using Only Lasso

Lasso Regression:

✅ Reduces Overfitting

✅ Performs Feature Selection

✅ Creates Sparsity

---

But sometimes:

```text
Lasso may remove too many features
```

and become unstable.

---

# Elastic Net Solution

Elastic Net combines:

```text
Ridge
+
Lasso
```

into a single model.

---

# What is Elastic Net Regression?

Elastic Net Regression is a regularized linear model that uses both:

```text
L1 Regularization
```

and

```text
L2 Regularization
```

simultaneously.

---

# Cost Function

```text
Cost

=

MSE

+

L1 Penalty

+

L2 Penalty
```

---

# Formula Idea

```text
Cost

=

MSE

+

λ₁Σ|m|

+

λ₂Σ(m²)
```

Where:

```text
MSE
=
Prediction Error

L1
=
Lasso Part

L2
=
Ridge Part
```

---

# Main Idea

Elastic Net wants:

✅ Smaller Coefficients

✅ Feature Selection

✅ Better Generalization

---

# Easy Memory

```text
Ridge
↓
Shrink

Lasso
↓
Shrink + Remove

Elastic Net
↓
Shrink + Remove + Balance
```

---

# Example

Original Coefficients:

```text
Area = 5000

Bedrooms = 3000

Garage = 1000

Pool = 500

Garden = 300
```

---

## Ridge

```text
Area = 500

Bedrooms = 300

Garage = 100

Pool = 50

Garden = 20
```

All remain.

---

## Lasso

```text
Area = 500

Bedrooms = 300

Garage = 0

Pool = 0

Garden = 0
```

Features removed.

---

## Elastic Net

```text
Area = 500

Bedrooms = 250

Garage = 50

Pool = 0

Garden = 0
```

Some coefficients shrink.

Some features are removed.

---

# What is l1_ratio?

The most important Elastic Net parameter.

It controls:

```text
How much Lasso?

How much Ridge?
```

---

## l1_ratio = 1

```text
Pure Lasso Regression
```

---

## l1_ratio = 0

```text
Pure Ridge Regression
```

---

## l1_ratio = 0.5

```text
50% Lasso

50% Ridge
```

---

# What is Alpha?

```text
Regularization Strength
```

Equivalent to:

```text
Lambda (λ)
```

---

## Small Alpha

```text
Weak Regularization
```

---

## Large Alpha

```text
Strong Regularization
```

---

## Very Large Alpha

```text
May Cause Underfitting
```

---

# Advantages

✅ Reduces Overfitting

✅ Performs Feature Selection

✅ Handles Correlated Features

✅ More Stable Than Lasso

✅ Combines Benefits Of Ridge And Lasso

---

# Disadvantages

❌ More Hyperparameters

❌ Needs Alpha Tuning

❌ Needs l1_ratio Tuning

❌ Slightly More Complex

---

# When To Use Elastic Net?

Use Elastic Net when:

✅ Dataset contains many features

✅ Features are highly correlated

✅ Overfitting exists

✅ Need both regularization and feature selection

✅ Lasso removes too many features

---

# sklearn Implementation

## Import

```python
from sklearn.linear_model import ElasticNet
```

---

## Create Model

```python
model = ElasticNet(
    alpha=1.0,
    l1_ratio=0.5
)
```

---

## Train

```python
model.fit(X_train, y_train)
```

---

## Predict

```python
y_pred = model.predict(X_test)
```

---

# Complete Code

```python
from sklearn.linear_model import ElasticNet

model = ElasticNet(
    alpha=1.0,
    l1_ratio=0.5,
    random_state=42
)

model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

---

# Check Coefficients

```python
print(model.coef_)
```

Example Output:

```text
[150, 90, 0, 0, 50]
```

Interpretation:

```text
Feature 3 removed

Feature 4 removed
```

because their coefficients became:

```text
0
```

---

# Elastic Net Using SGD

```python
from sklearn.linear_model import SGDRegressor

elastic_net = SGDRegressor(
    penalty='elasticnet',
    alpha=0.0001,
    l1_ratio=0.5,
    learning_rate='constant',
    eta0=0.01,
    max_iter=1000,
    random_state=42
)

elastic_net.fit(X_train, y_train)

y_pred = elastic_net.predict(X_test)
```

---

# Important SGD Parameters

## penalty='elasticnet'

```text
Elastic Net Regularization
```

---

## alpha

```text
Regularization Strength
```

---

## l1_ratio

```text
Controls Lasso vs Ridge Balance
```

---

## eta0

```text
Learning Rate
```

---

## max_iter

```text
Maximum Epochs
```

---

# Ridge vs Lasso vs Elastic Net

| Property | Ridge | Lasso | Elastic Net |
|-----------|--------|--------|-------------|
| Regularization | L2 | L1 | L1 + L2 |
| Shrinks Coefficients | ✅ | ✅ | ✅ |
| Feature Selection | ❌ | ✅ | ✅ |
| Creates Sparsity | ❌ | ✅ | ✅ |
| Keeps All Features | ✅ | ❌ | ❌ |
| Handles Correlated Features | ✅ | Limited | ✅ |

---

# Real Machine Learning Workflow

```text
Preprocessing
↓
Linear Regression
↓
Check Train/Test Score
```

---

## Underfitting

```text
Train Low

Test Low
```

↓

```text
Polynomial Regression
```

---

## Overfitting

```text
Train High

Test Much Lower
```

↓

```text
Ridge

or

Lasso

or

Elastic Net
```

---

## Need Feature Selection

↓

```text
Lasso
```

---

## Need Feature Selection + Coefficient Shrinking

↓

```text
Elastic Net
```

---

# Interview Questions

## What is Elastic Net Regression?

Elastic Net Regression is a regularized linear model that combines L1 and L2 regularization.

---

## Why do we use Elastic Net?

To get the benefits of both Ridge and Lasso Regression.

---

## What does l1_ratio do?

It controls the balance between L1 and L2 regularization.

---

## What happens when l1_ratio = 1?

Elastic Net becomes Lasso Regression.

---

## What happens when l1_ratio = 0?

Elastic Net becomes Ridge Regression.

---

## Which sklearn class is used for Elastic Net?

```python
ElasticNet()
```

---

## Which SGD penalty corresponds to Elastic Net?

```python
penalty='elasticnet'
```

---

# Revision Notes

```text
Elastic Net
↓
Ridge + Lasso

Regularization
↓
L1 + L2

Purpose
↓
Reduce Overfitting

Shrink Coefficients
↓
Yes

Feature Selection
↓
Yes

alpha
↓
Regularization Strength

l1_ratio
↓
Lasso vs Ridge Balance

l1_ratio = 1
↓
Lasso

l1_ratio = 0
↓
Ridge
```

---

# Summary

Elastic Net Regression is a regularized version of Linear Regression that combines the strengths of Ridge Regression and Lasso Regression.

It reduces overfitting, shrinks coefficient values, performs feature selection, and is particularly useful when working with datasets that contain many correlated features.

Elastic Net is often considered a balanced approach because it provides the advantages of both Ridge and Lasso in a single model.

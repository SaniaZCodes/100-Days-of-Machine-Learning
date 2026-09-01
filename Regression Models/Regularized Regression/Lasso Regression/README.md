# Lasso Regression

# Overview

Lasso Regression (Least Absolute Shrinkage and Selection Operator) is a regularized version of Linear Regression.

It is used to:

✅ Reduce Overfitting

✅ Improve Generalization

✅ Perform Automatic Feature Selection

---

# Why Do We Need Lasso Regression?

Sometimes Linear Regression overfits the training data.

Example:

```text
Train R² = 0.99

Test R² = 0.72
```

This indicates:

```text
Overfitting
```

We need a technique that:

```text
Controls Model Complexity
```

Lasso Regression solves this problem.

---

# What is Regularization?

Regularization is a technique used to reduce overfitting by adding a penalty term to the cost function.

---

# What is Lasso Regression?

Lasso Regression is a regularized version of Linear Regression that adds an L1 penalty to the cost function.

---

# Linear Regression Cost Function

```text
Cost = MSE
```

---

# Lasso Regression Cost Function

```text
Cost = MSE + λΣ|m|
```

---

# Formula Explanation

## MSE

Measures prediction error.

---

## λ (Lambda)

Regularization strength.

Controls penalty amount.

---

## Σ|m|

Sum of absolute coefficient values.

Example:

```text
|5| + |3| + |2|

=

10
```

---

# What is L1 Regularization?

Lasso Regression uses:

```text
L1 Regularization
```

Penalty:

```text
Σ|m|
```

Easy Memory:

```text
Lasso
↓
L1
↓
Absolute Value
```

---

# Main Idea

Lasso not only reduces coefficient values but can completely remove features.

---

# Example

Before Lasso:

```text
Area      = 5000

Bedrooms  = 3000

Garage    = 1000

Pool      = 500

Garden    = 300
```

---

After Lasso:

```text
Area      = 500

Bedrooms  = 200

Garage    = 0

Pool      = 0

Garden    = 0
```

Notice:

```text
Garage

Pool

Garden
```

have become:

```text
0
```

These features are effectively removed.

---

# Feature Selection

Lasso automatically decides:

```text
Which Features Are Important
```

and

```text
Which Features Are Useless
```

This process is called:

```text
Feature Selection
```

---

# What is Sparsity?

Sparsity means:

```text
Many Coefficients Become Zero
```

Example:

```text
[500, 200, 0, 0, 0]
```

The model only uses important features.

---

# Why Does Lasso Create Sparsity?

Because Lasso uses:

```text
L1 Regularization
```

which can force coefficient values to become exactly:

```text
0
```

Once a coefficient becomes:

```text
0
```

the corresponding feature is removed from the model.

---

# Ridge vs Lasso

| Property | Ridge | Lasso |
|-----------|---------|---------|
| Regularization Type | L2 | L1 |
| Penalty | m² | \|m\| |
| Reduces Overfitting | ✅ | ✅ |
| Shrinks Coefficients | ✅ | ✅ |
| Feature Selection | ❌ | ✅ |
| Creates Sparsity | ❌ | ✅ |

---

# Ridge Example

Before:

```text
5000

3000

1000

500
```

After Ridge:

```text
500

300

100

50
```

All features remain.

---

# Lasso Example

Before:

```text
5000

3000

1000

500
```

After Lasso:

```text
500

300

0

0
```

Some features are removed.

---

# When Should We Use Lasso?

Use Lasso when:

✅ Overfitting exists

✅ Dataset contains many features

✅ Some features may be useless

✅ Feature selection is required

---

# Advantages

✅ Reduces Overfitting

✅ Automatic Feature Selection

✅ Creates Simpler Models

✅ Improves Interpretability

✅ Reduces Number of Features

---

# Disadvantages

❌ Can remove useful features

❌ Sensitive to Lambda value

❌ May underfit if regularization is too strong

---

# sklearn Implementation

## Import Model

```python
from sklearn.linear_model import Lasso
```

---

## Create Model

```python
lasso = Lasso(alpha=1.0)
```

---

## Train Model

```python
lasso.fit(X_train, y_train)
```

---

## Prediction

```python
y_pred = lasso.predict(X_test)
```

---

# Complete sklearn Code

```python
from sklearn.linear_model import Lasso

lasso = Lasso(alpha=1.0)

lasso.fit(X_train, y_train)

y_pred = lasso.predict(X_test)
```

---

# Check Coefficients

```python
print(lasso.coef_)
```

Example Output:

```text
[120, 50, 0, 0, 200]
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

# Lasso Using SGD

```python
from sklearn.linear_model import SGDRegressor

lasso_sgd = SGDRegressor(
    penalty='l1',
    alpha=0.0001,
    learning_rate='constant',
    eta0=0.01,
    max_iter=1000,
    random_state=42
)

lasso_sgd.fit(X_train, y_train)

y_pred = lasso_sgd.predict(X_test)
```

---

# Understanding SGD Parameters

## penalty='l1'

```text
Use Lasso Regularization
```

---

## alpha

```text
Regularization Strength
```

Equivalent to Lambda.

---

## eta0

```text
Learning Rate
```

Step size during gradient updates.

---

## max_iter

```text
Maximum Epochs
```

---

# Real ML Workflow

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
Train Very High

Test Much Lower
```

↓

```text
Ridge Regression
```

or

```text
Lasso Regression
```

---

## Many Useless Features

↓

```text
Lasso Regression
```

because Lasso performs Feature Selection.

---

# Interview Questions

## What is Lasso Regression?

Lasso Regression is a regularized Linear Regression model that uses L1 regularization to reduce overfitting and perform feature selection.

---

## What is L1 Regularization?

L1 regularization adds the absolute values of coefficients to the cost function.

---

## What is Sparsity?

Sparsity means that many coefficients become exactly zero.

---

## Why Does Lasso Create Sparsity?

Because L1 regularization can force some coefficients to become

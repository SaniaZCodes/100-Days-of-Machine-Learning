# Gradient Descent and Its Types

## Overview

Gradient Descent is an optimization algorithm used to minimize a model's error by finding the best values of model parameters.

In Linear Regression, Gradient Descent helps find the optimal values of:

```text
m (Slope)
c (Intercept)
```

that minimize the cost function.

---

# What is Gradient Descent?

Gradient Descent is an optimization algorithm that minimizes a cost function by iteratively updating model parameters in the direction of minimum error.

In simple words:

> Gradient Descent helps a machine learning model learn the best parameters.

---

# Why Do We Need Gradient Descent?

Suppose we have a Linear Regression model:

```text
Y = mX + c
```

The challenge is:

```text
How do we find the best values of m and c?
```

Gradient Descent solves this problem.

---

# Goal of Gradient Descent

```text
Find Best Parameters
↓
Minimize Error
↓
Improve Predictions
```

---

# Cost Function

Gradient Descent minimizes a cost function.

For Linear Regression, the most common cost function is:

```text
MSE (Mean Squared Error)
```

The objective is:

```text
Minimum MSE
```

---

# What is a Gradient?

Gradient tells us:

> Which direction should we move to reduce error?

In simple words:

```text
Gradient
↓
Direction Indicator
```

If error increases:

```text
Move in the opposite direction.
```

If error decreases:

```text
Keep moving.
```

---

# What is Convergence?

Convergence means:

> The process of reaching the minimum error solution.

Example:

```text
Error = 1000
↓
500
↓
100
↓
10
↓
2
↓
1.9
↓
1.89
```

Eventually the model reaches the minimum and stops.

This is called convergence.

---

# What is Learning Rate?

Learning Rate controls the size of each step during parameter updates.

Symbol:

```text
α (alpha)
```

---

## Small Learning Rate

```text
Tiny Steps
```

Advantages:

- More accurate

Disadvantages:

- Slow training

---

## Large Learning Rate

```text
Huge Steps
```

Advantages:

- Faster updates

Disadvantages:

- May overshoot the minimum
- May never converge

---

# What is an Epoch?

An Epoch is one complete pass through the entire training dataset.

Example:

Dataset:

```text
1000 Rows
```

If the model processes all 1000 rows once:

```text
1 Epoch Completed
```

If the model processes all rows 10 times:

```text
10 Epochs
```

---

# Types of Gradient Descent

1. Batch Gradient Descent
2. Stochastic Gradient Descent (SGD)
3. Mini-Batch Gradient Descent

---

# 1. Batch Gradient Descent

## What is Batch Gradient Descent?

Batch Gradient Descent uses the entire dataset before updating model parameters.

Workflow:

```text
All Rows
↓
Calculate Gradient
↓
Update Parameters
```

---

## Example

Dataset:

```text
1000 Rows
```

Batch GD:

```text
All 1000 Rows
↓
1 Update
```

---

## Advantages

✅ Stable Learning

✅ Accurate Gradient

✅ Smooth Convergence

---

## Disadvantages

❌ Slow

❌ High Memory Usage

❌ Expensive for Large Datasets

---

## When to Use?

- Small to medium datasets
- When stability is important

---

# 2. Stochastic Gradient Descent (SGD)

## What is SGD?

Stochastic Gradient Descent updates model parameters after processing a single training example.

Workflow:

```text
1 Row
↓
Update Parameters

1 Row
↓
Update Parameters
```

---

## Example

Dataset:

```text
1000 Rows
```

SGD:

```text
Row 1
↓
Update

Row 2
↓
Update

Row 3
↓
Update
```

---

## Advantages

✅ Very Fast

✅ Low Memory Usage

✅ Suitable for Huge Datasets

---

## Disadvantages

❌ Noisy Updates

❌ Zig-Zag Convergence

❌ Less Stable

---

## When to Use?

- Very Large Datasets
- Online Learning Systems

---

# 3. Mini-Batch Gradient Descent

## What is Mini-Batch Gradient Descent?

Mini-Batch Gradient Descent updates model parameters using a small group of training examples.

Workflow:

```text
Small Batch
↓
Update Parameters
```

---

## Example

Dataset:

```text
10000 Rows
```

Batch Size:

```text
100
```

Workflow:

```text
100 Rows
↓
Update

100 Rows
↓
Update

100 Rows
↓
Update
```

---

## Advantages

✅ Faster Than Batch GD

✅ More Stable Than SGD

✅ Less Memory Usage

✅ Most Commonly Used

---

## Disadvantages

❌ Requires Batch Size Selection

❌ Still Has Some Noise

---

## When to Use?

- Medium to Large Datasets
- Deep Learning
- Neural Networks

---

# Comparison

| Method | Data Used Per Update | Speed | Stability |
|----------|----------|----------|----------|
| Batch GD | Entire Dataset | Slow | High |
| SGD | One Sample | Fast | Low |
| Mini-Batch GD | Small Batch | Fast | Good |

---

# Easy Memory

```text
Batch GD
↓
All Rows

SGD
↓
One Row

Mini-Batch GD
↓
Small Group of Rows
```

---

# sklearn Code

## Batch Gradient Descent

Scikit-learn's LinearRegression internally uses optimization methods and is typically treated as the batch-style learning approach.

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()

model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

---

## Stochastic Gradient Descent (SGD)

```python
from sklearn.linear_model import SGDRegressor

model = SGDRegressor(
    max_iter=1000,
    learning_rate='constant',
    eta0=0.01,
    random_state=42
)

model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

---

## Mini-Batch Gradient Descent

Scikit-learn does not provide a direct MiniBatchRegressor for linear regression.

Mini-batch training is commonly used in deep learning frameworks such as:

- TensorFlow
- PyTorch
- Keras

Example Concept:

```python
for batch in mini_batches:
    model.train(batch)
```

---

# Important Terms

## Cost Function

Measures prediction error.

Example:

```text
MSE
```

---

## Gradient

Direction of error reduction.

---

## Learning Rate

Step size during updates.

---


# Understanding the sklearn Code

## Batch Gradient Descent

### Code

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()

model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

### Explanation

```python
from sklearn.linear_model import LinearRegression
```

Imports the Linear Regression model from scikit-learn.

---

```python
model = LinearRegression()
```

Creates an empty Linear Regression model.

At this stage, the model does not know anything about the data.

---

```python
model.fit(X_train, y_train)
```

Trains the model.

During training:

- Features are taken from X_train
- Target values are taken from y_train
- Model learns the best coefficients
- Model learns the best intercept

Goal:

```text
Minimize Error
```

---

```python
y_pred = model.predict(X_test)
```

Uses learned coefficients to make predictions on unseen data.

---

# Stochastic Gradient Descent (SGD)

### Code

```python
from sklearn.linear_model import SGDRegressor

model = SGDRegressor(
    max_iter=1000,
    learning_rate='constant',
    eta0=0.01,
    random_state=42
)

model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

---

## Explanation

```python
from sklearn.linear_model import SGDRegressor
```

Imports the SGD Regression model.

This model learns using:

```text
Stochastic Gradient Descent
```

instead of the standard Linear Regression optimization method.

---

```python
max_iter=1000
```

Maximum number of epochs.

Meaning:

```text
Dataset can be processed
up to 1000 times
```

if needed.

---

```python
learning_rate='constant'
```

Learning rate remains fixed throughout training.

---

```python
eta0=0.01
```

Initial learning rate.

This controls:

```text
Step Size
```

during parameter updates.

---

```python
random_state=42
```

Ensures reproducible results.

Running the code again gives the same output.

---

```python
model.fit(X_train, y_train)
```

Training starts.

For every training sample:

```text
Calculate Error
↓
Calculate Gradient
↓
Update Parameters
```

---

```python
y_pred = model.predict(X_test)
```

Generates predictions.

---

# Accessing Coefficients

### Code

```python
print(model.coef_)
```

### Explanation

Displays the learned coefficients.

Example:

```text
[120, 8000]
```

Means:

```text
Area coefficient = 120

Bedroom coefficient = 8000
```

---

# Accessing Intercept

### Code

```python
print(model.intercept_)
```

### Explanation

Displays the intercept.

Example:

```text
10000
```

Meaning:

When all feature values become zero,

Prediction:

```text
10000
```

---

# Mini-Batch Gradient Descent

## Code

```python
from sklearn.linear_model import SGDRegressor

model = SGDRegressor(
    learning_rate='constant',
    eta0=0.01,
    random_state=42
)

batch_size = 100

for i in range(0, len(X_train), batch_size):

    X_batch = X_train[i:i+batch_size]
    y_batch = y_train[i:i+batch_size]

    model.partial_fit(X_batch, y_batch)

y_pred = model.predict(X_test)
```

---

## Explanation

```python
batch_size = 100
```

Mini-batch size is 100.

Meaning:

```text
100 rows
↓
One Update
```

---

```python
for i in range(...)
```

Iterates over the dataset in small chunks.

---

```python
X_batch
```

Stores the current batch features.

---

```python
y_batch
```

Stores the current batch target values.

---

```python
partial_fit()
```

Updates model parameters using only the current batch.

This is the key function that creates Mini-Batch Gradient Descent behaviour.

---

```python
predict()
```

Makes predictions on unseen data.

---

# Quick Comparison

```text
LinearRegression()
↓
Simple / Multiple Linear Regression
```

```text
SGDRegressor()
↓
Stochastic Gradient Descent
```

```text
SGDRegressor() + partial_fit()
↓
Mini-Batch Gradient Descent
```

---

# Interview Questions

Q. What is SGDRegressor?

Answer:

A regression model that learns using Stochastic Gradient Descent.

---

Q. What does max_iter represent?

Answer:

Maximum number of epochs.

---

Q. What does eta0 represent?

Answer:

Initial learning rate.

---

Q. Which function is used for Mini-Batch training?

Answer:

```python
partial_fit()
```

---

Q. Which sklearn class implements SGD?

Answer:

```python
SGDRegressor
```

---

## Epoch

One complete pass through the entire dataset.

---


# Understanding the sklearn Code

## Batch Gradient Descent

### Code

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()

model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

### Explanation

```python
from sklearn.linear_model import LinearRegression
```

Imports the Linear Regression model from scikit-learn.

---

```python
model = LinearRegression()
```

Creates an empty Linear Regression model.

At this stage, the model does not know anything about the data.

---

```python
model.fit(X_train, y_train)
```

Trains the model.

During training:

- Features are taken from X_train
- Target values are taken from y_train
- Model learns the best coefficients
- Model learns the best intercept

Goal:

```text
Minimize Error
```

---

```python
y_pred = model.predict(X_test)
```

Uses learned coefficients to make predictions on unseen data.

---

# Stochastic Gradient Descent (SGD)

### Code

```python
from sklearn.linear_model import SGDRegressor

model = SGDRegressor(
    max_iter=1000,
    learning_rate='constant',
    eta0=0.01,
    random_state=42
)

model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

---

## Explanation

```python
from sklearn.linear_model import SGDRegressor
```

Imports the SGD Regression model.

This model learns using:

```text
Stochastic Gradient Descent
```

instead of the standard Linear Regression optimization method.

---

```python
max_iter=1000
```

Maximum number of epochs.

Meaning:

```text
Dataset can be processed
up to 1000 times
```

if needed.

---

```python
learning_rate='constant'
```

Learning rate remains fixed throughout training.

---

```python
eta0=0.01
```

Initial learning rate.

This controls:

```text
Step Size
```

during parameter updates.

---

```python
random_state=42
```

Ensures reproducible results.

Running the code again gives the same output.

---

```python
model.fit(X_train, y_train)
```

Training starts.

For every training sample:

```text
Calculate Error
↓
Calculate Gradient
↓
Update Parameters
```

---

```python
y_pred = model.predict(X_test)
```

Generates predictions.

---

# Accessing Coefficients

### Code

```python
print(model.coef_)
```

### Explanation

Displays the learned coefficients.

Example:

```text
[120, 8000]
```

Means:

```text
Area coefficient = 120

Bedroom coefficient = 8000
```

---

# Accessing Intercept

### Code

```python
print(model.intercept_)
```

### Explanation

Displays the intercept.

Example:

```text
10000
```

Meaning:

When all feature values become zero,

Prediction:

```text
10000
```

---

# Mini-Batch Gradient Descent

## Code

```python
from sklearn.linear_model import SGDRegressor

model = SGDRegressor(
    learning_rate='constant',
    eta0=0.01,
    random_state=42
)

batch_size = 100

for i in range(0, len(X_train), batch_size):

    X_batch = X_train[i:i+batch_size]
    y_batch = y_train[i:i+batch_size]

    model.partial_fit(X_batch, y_batch)

y_pred = model.predict(X_test)
```

---

## Explanation

```python
batch_size = 100
```

Mini-batch size is 100.

Meaning:

```text
100 rows
↓
One Update
```

---

```python
for i in range(...)
```

Iterates over the dataset in small chunks.

---

```python
X_batch
```

Stores the current batch features.

---

```python
y_batch
```

Stores the current batch target values.

---

```python
partial_fit()
```

Updates model parameters using only the current batch.

This is the key function that creates Mini-Batch Gradient Descent behaviour.

---

```python
predict()
```

Makes predictions on unseen data.

---

# Quick Comparison

```text
LinearRegression()
↓
Simple / Multiple Linear Regression
```

```text
SGDRegressor()
↓
Stochastic Gradient Descent
```

```text
SGDRegressor() + partial_fit()
↓
Mini-Batch Gradient Descent
```

---

# Interview Questions

Q. What is SGDRegressor?

Answer:

A regression model that learns using Stochastic Gradient Descent.

---

Q. What does max_iter represent?

Answer:

Maximum number of epochs.

---

Q. What does eta0 represent?

Answer:

Initial learning rate.

---

Q. Which function is used for Mini-Batch training?

Answer:

```python
partial_fit()
```

---

Q. Which sklearn class implements SGD?

Answer:

```python
SGDRegressor
```

# 🌳 Decision Trees

## 📌 Overview

Decision Tree is a supervised machine learning algorithm used for both Classification and Regression problems.

It works by recursively splitting the data into smaller subsets using a series of questions. The objective is to create groups that are as pure as possible.

Decision Trees are easy to understand, easy to visualize, and closely resemble human decision-making.

---

# 🎯 What is a Decision Tree?

A Decision Tree makes predictions by asking a sequence of questions.

Example:

```text
Chest Pain?

├── Yes
│   └── Disease
│
└── No
    └── No Disease
```

The algorithm continues asking questions until it reaches a final decision.

---

# 🌳 Components of a Decision Tree

## Root Node

The first question asked by the tree.

Example:

```text
Chest Pain?
```

---

## Internal Node

An intermediate decision point.

Example:

```text
Age > 50?
```

---

## Leaf Node

Final prediction node.

Example:

```text
Disease

No Disease
```

---

# 🎯 Goal of Decision Tree

The primary goal of a Decision Tree is:

```text
Reduce Confusion
```

and create the purest possible groups.

---

# 📊 Entropy

Entropy measures the amount of randomness or impurity in a node.

### Pure Node

```text
Disease
Disease
Disease
Disease
```

Entropy:

```text
0
```

✅ Good

---

### Impure Node

```text
Disease
No Disease
Disease
No Disease
```

Entropy:

```text
High
```

❌ Bad

---

## Easy Interpretation

```text
Low Entropy
↓
Less Confusion

High Entropy
↓
More Confusion
```

---

# 📊 Gini Impurity

Gini Impurity is another measure of impurity.

Like Entropy, it measures how mixed a node is.

### Pure Node

```text
Disease
Disease
Disease
```

Gini:

```text
0
```

✅ Good

---

### Mixed Node

```text
Disease
No Disease
Disease
No Disease
```

Gini:

```text
High
```

❌ Bad

---

# 📊 Information Gain

Information Gain measures how much impurity is reduced after a split.

Formula:

```text
Information Gain

=

Impurity Before Split

-

Impurity After Split
```

The higher the Information Gain, the better the split.

---

# 🎯 Tree Building Strategy

Decision Tree:

1. Calculates impurity for all features.
2. Tries different splits.
3. Computes Information Gain.
4. Selects the feature with Maximum Information Gain.
5. Repeats the process recursively.

---

# 🌳 Overfitting in Decision Trees

A tree can continue growing until it memorizes the training data.

Symptoms:

✅ High Training Accuracy

❌ Low Testing Accuracy

This is called:

```text
Overfitting
```

---

# 🌳 Underfitting

A very small tree may fail to learn important patterns.

Symptoms:

❌ Low Training Accuracy

❌ Low Testing Accuracy

This is called:

```text
Underfitting
```

---

# ⚙️ Important Hyperparameters

## 1. max_depth

Controls the maximum depth of the tree.

### Small Value

```python
max_depth=2
```

May cause:

```text
Underfitting
```

### Large Value

```python
max_depth=20
```

May cause:

```text
Overfitting
```

---

## 2. min_samples_split

Minimum number of records required before a node can split.

Example:

```python
min_samples_split=10
```

A node must contain at least 10 samples before creating child nodes.

---

## 3. min_samples_leaf

Minimum number of records required in every leaf node.

Example:

```python
min_samples_leaf=5
```

Each final leaf must contain at least 5 records.

---

## 4. max_leaf_nodes

Maximum number of leaf nodes allowed in the tree.

Example:

```python
max_leaf_nodes=20
```

The tree stops creating leaves after reaching this limit.

---

# 🌳 Classification Tree

Classification Trees predict categories.

Examples:

```text
Disease / No Disease

Spam / Not Spam

Pass / Fail
```

The prediction at a leaf node is the majority class.

---

# 🌳 Regression Tree

Regression Trees predict numerical values.

Examples:

```text
House Price

Salary

Temperature
```

The prediction at a leaf node is the average value of observations in that leaf.

---

# 📊 Classification Tree vs Regression Tree

## Classification Tree

Predicts:

```text
Classes
```

Uses:

```text
Entropy

Gini Impurity

Information Gain
```

Leaf Prediction:

```text
Majority Class
```

---

## Regression Tree

Predicts:

```text
Numbers
```

Uses:

```text
Variance Reduction

MSE
```

Leaf Prediction:

```text
Mean Value
```

---

# ✅ Advantages of Decision Trees

- Easy to understand
- Easy to visualize
- Works for Classification and Regression
- Handles non-linear relationships
- Requires little preprocessing
- Feature scaling is not required

---

# ❌ Disadvantages of Decision Trees

- Can overfit easily
- Sensitive to small data changes
- Can create overly complex trees
- Lower performance compared to ensemble methods

---

# ⚠️ Feature Scaling

Decision Trees do not depend on distance calculations.

Therefore:

```text
Feature Scaling is NOT required.
```

---

# 🤖 Decision Tree Classifier (Scikit-Learn)

## Import Library

```python
from sklearn.tree import DecisionTreeClassifier
```

---

## Create Model

```python
dt = DecisionTreeClassifier()
```

---

## Train Model

```python
dt.fit(X_train, Y_train)
```

---

## Make Predictions

```python
Y_pred_dt = dt.predict(X_test)
```

---

# 🌳 Decision Tree Classifier with Hyperparameters

```python
from sklearn.tree import DecisionTreeClassifier

dt = DecisionTreeClassifier(
    criterion='gini',
    max_depth=3,
    min_samples_split=5,
    min_samples_leaf=2,
    max_leaf_nodes=15,
    random_state=42
)

dt.fit(X_train, Y_train)

Y_pred_dt = dt.predict(X_test)
```

---

# 📈 Tree Visualization

```python
from sklearn.tree import plot_tree
import matplotlib.pyplot as plt

plt.figure(figsize=(20,10))

plot_tree(
    dt,
    feature_names=X.columns,
    class_names=["No Disease", "Disease"],
    filled=True,
    rounded=True,
    fontsize=10
)

plt.show()
```

---

# 📊 Feature Importance

```python
import pandas as pd

importance_df = pd.DataFrame({
    "Feature": X.columns,
    "Importance": dt.feature_importances_
})

importance_df.sort_values(
    by="Importance",
    ascending=False
)
```

This helps identify the most important features used by the tree.

---

# 🎯 Interview Questions

### What is a Decision Tree?

A supervised learning algorithm that makes predictions using a series of decision rules.

---

### What is Entropy?

A measure of randomness or impurity in a node.

---

### What is Gini Impurity?

A measure used to evaluate the impurity of a node.

---

### What is Information Gain?

The reduction in impurity after a split.

---

### Which split does a Decision Tree choose?

The split with the highest Information Gain.

---

### What causes Overfitting in Decision Trees?

Excessive tree growth and memorization of training data.

---

### Which hyperparameter is most important?

```text
max_depth
```

---

### Do Decision Trees require Feature Scaling?

```text
No
```

---

### What is the prediction in a Regression Tree leaf?

The mean value of observations in that leaf.

---

# 📝 Key Takeaways

✅ Decision Trees use a tree-like structure for prediction

✅ Root Node represents the first split

✅ Entropy and Gini measure impurity

✅ Information Gain measures impurity reduction

✅ Decision Trees choose the split with maximum Information Gain

✅ max_depth helps control overfitting

✅ Classification Trees predict classes

✅ Regression Trees predict continuous values

✅ Regression Trees use mean values at leaf nodes

✅ Feature scaling is not required

✅ Easy to visualize and interpret

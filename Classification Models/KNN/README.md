# 🤖 K-Nearest Neighbors (KNN)

## 📌 Overview

K-Nearest Neighbors (KNN) is a supervised machine learning algorithm used for both classification and regression tasks.

KNN predicts the class of a new data point by looking at the classes of its nearest neighbors and selecting the majority class.

Unlike many machine learning algorithms, KNN does not learn a mathematical model during training. Instead, it stores the training data and performs computations only when a prediction is required.

Because of this behavior, KNN is known as a **Lazy Learning Algorithm**.

---

# 🎯 What is KNN?

KNN stands for:

```text
K = Number of Neighbors

Nearest = Closest

Neighbors = Data Points
```

The algorithm predicts a class by examining the K closest training examples to a new observation.

---

# 🧠 Intuition Behind KNN

Suppose a new data point is added to the dataset.

The algorithm:

1. Calculates the distance between the new point and all training points.
2. Finds the K nearest neighbors.
3. Counts the class labels of those neighbors.
4. Assigns the majority class.

Example:

```text
K = 3

Neighbors:

🔴
🔴
🔵
```

Vote Count:

```text
Red  = 2

Blue = 1
```

Prediction:

```text
🔴 Red
```

---

# 🔢 What is K?

K represents the number of nearest neighbors used for prediction.

Examples:

```text
K = 1

Only the closest point is considered.
```

```text
K = 3

Three nearest points are considered.
```

```text
K = 5

Five nearest points are considered.
```

### Choosing K

Small K:

```text
High Variance

Sensitive to Noise
```

Large K:

```text
High Bias

May ignore local patterns
```

Common choices:

```text
K = 3

K = 5

K = 7
```

---

# 📏 Distance Calculation

KNN works by measuring distances between data points.

The most commonly used distance metric is:

## Euclidean Distance

Formula:

```text
√[(x₁ − x₂)² + (y₁ − y₂)²]
```

It represents the straight-line distance between two points.

---

# ⚠️ Why Feature Scaling is Important

KNN relies entirely on distance calculations.

Consider:

```text
Age     = 25

Salary  = 50000
```

Without scaling:

```text
Salary dominates the distance calculation.
```

As a result, the model becomes biased.

Therefore:

✅ Feature Scaling is highly recommended before applying KNN.

Common Scaling Methods:

- Standardization
- Normalization

---

# 🔄 Working of KNN

Step 1:

```text
Store Training Data
```

Step 2:

```text
Receive New Data Point
```

Step 3:

```text
Calculate Distance From All Training Points
```

Step 4:

```text
Find K Nearest Neighbors
```

Step 5:

```text
Perform Majority Voting
```

Step 6:

```text
Assign Predicted Class
```

---

# 📊 KNN for Classification

In classification problems:

```text
Prediction = Majority Vote
```

Example:

```text
Neighbors:

Class 1
Class 1
Class 0
Class 1
Class 0
```

Votes:

```text
Class 1 = 3

Class 0 = 2
```

Prediction:

```text
Class 1
```

---

# 📈 KNN for Regression

KNN can also be used for regression problems.

Instead of majority voting:

```text
Average of Neighbor Values
```

Example:

```text
Neighbor Values:

100

110

120
```

Prediction:

```text
(100 + 110 + 120) / 3

= 110
```

---

# ✅ Advantages of KNN

- Easy to understand and implement
- No training phase required
- Works well on small datasets
- Can handle non-linear decision boundaries
- Can be used for both classification and regression

---

# ❌ Disadvantages of KNN

- Slow prediction on large datasets
- Computationally expensive
- Sensitive to noise
- Requires feature scaling
- Performance decreases with high-dimensional data

---

# 🤖 KNN Using Scikit-Learn

## Import Library

```python
from sklearn.neighbors import KNeighborsClassifier
```

---

## Create Model

```python
knn = KNeighborsClassifier(
    n_neighbors=5
)
```

---

## Train Model

```python
knn.fit(X_train_scaled, Y_train)
```

---

## Make Predictions

```python
Y_pred_knn = knn.predict(X_test_scaled)
```

---

## Complete Example

```python
from sklearn.neighbors import KNeighborsClassifier

# Create Model
knn = KNeighborsClassifier(n_neighbors=5)

# Train Model
knn.fit(X_train_scaled, Y_train)

# Predictions
Y_pred_knn = knn.predict(X_test_scaled)
```

---

# 🎯 Interview Questions

### What is KNN?

KNN is a supervised machine learning algorithm that predicts a new data point using the majority class of its nearest neighbors.

---

### Why is KNN called a Lazy Learner?

Because it does not learn a model during training and simply stores the training dataset.

---

### What does K represent?

K represents the number of nearest neighbors considered during prediction.

---

### Why is Feature Scaling important in KNN?

Because KNN depends on distance calculations and features with larger values can dominate the distance metric.

---

### Can KNN perform Regression?

Yes.

KNN supports both:

- Classification
- Regression

---

### Which distance metric is commonly used?

Euclidean Distance.

---

# 📝 Key Takeaways

✅ KNN is a Distance-Based Algorithm

✅ K represents Number of Neighbors

✅ Prediction is based on Majority Voting

✅ Euclidean Distance is commonly used

✅ Feature Scaling is very important

✅ KNN is a Lazy Learning Algorithm

✅ Works for both Classification and Regression

✅ Simple but effective on small datasets

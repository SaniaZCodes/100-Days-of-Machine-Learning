# 🤖 K-Means Clustering

## 📌 Overview

K-Means is one of the most popular Unsupervised Machine Learning algorithms used for clustering.

Unlike Supervised Learning, K-Means does not require a target variable. Instead, it automatically discovers hidden patterns in data by grouping similar observations into clusters.

The goal of K-Means is to partition data into K distinct clusters where observations within the same cluster are more similar to each other than to observations in other clusters.

---

# 🎯 What is Unsupervised Learning?

In Unsupervised Learning, there is no target variable.

### Supervised Learning

```text
Features (X)
+
Target (Y)
```

Example:

```text
Age
BMI
Glucose
↓
Diabetes
```

---

### Unsupervised Learning

```text
Features (X)

No Target Variable
```

Example:

```text
Age
Income
Spending Score
```

The algorithm must find patterns automatically.

---

# 📚 What is Clustering?

Clustering is the process of grouping similar observations together.

Example:

```text
Customer Group 1

Young
High Spending
```

```text
Customer Group 2

Older
Low Spending
```

These groups are called:

```text
Clusters
```

---

# 🔤 What is K?

K represents:

```text
Number of Clusters
```

Example:

```text
K = 2
```

Means:

```text
Create 2 clusters
```

---

```text
K = 3
```

Means:

```text
Create 3 clusters
```

---

# 🎯 What is a Centroid?

A Centroid is the center point of a cluster.

Think of it as:

```text
Representative Point
```

for a group.

Example:

Cluster:

```text
40
42
45
```

Centroid:

```text
(40 + 42 + 45) / 3

= 42.33
```

---

# ⚙️ How K-Means Works

K-Means repeatedly performs two operations:

### Step 1

Assign data points to the nearest centroid.

### Step 2

Update centroids using the mean of assigned points.

This process continues until centroids stop moving.

---

# 🔄 K-Means Algorithm

## Step 1: Choose K

Select the number of clusters.

Example:

```text
K = 3
```

---

## Step 2: Initialize Centroids

Randomly place K centroids.

Example:

```text
C1

C2

C3
```

---

## Step 3: Assign Points

Assign each observation to the nearest centroid.

---

## Step 4: Update Centroids

Calculate the mean of each cluster and update centroid positions.

---

## Step 5: Repeat

Repeat:

```text
Assign Points
      ↓

Update Centroids
      ↓

Assign Again
      ↓

Update Again
```

until centroids stop changing.

---

# 🎯 Convergence

K-Means stops when:

```text
Centroids stop moving
```

This state is called:

```text
Convergence
```

At convergence:

✅ Clusters become stable

✅ Centroids no longer change significantly

---

# 📊 What is WCSS?

WCSS stands for:

```text
Within Cluster Sum of Squares
```

It measures how close observations are to their cluster centroid.

### Small WCSS

```text
Points are close to centroid
```

✅ Good clustering

---

### Large WCSS

```text
Points are far from centroid
```

❌ Poor clustering

---

# 🎯 Why Do We Need WCSS?

K-Means requires us to choose:

```text
K
```

But how do we know the right value?

WCSS helps us evaluate cluster quality.

---

# 📈 Elbow Method

The Elbow Method is used to determine the optimal value of K.

### Procedure

1. Run K-Means for different values of K.

Example:

```text
K = 1

K = 2

K = 3

K = 4

K = 5
```

2. Calculate WCSS for each K.

3. Plot:

```text
K vs WCSS
```

4. Look for the bend in the graph.

This bend is called:

```text
Elbow Point
```

---

# ✅ Why Elbow Point?

The elbow represents the point where increasing K provides only small improvements.

The corresponding K is usually selected as the optimal number of clusters.

---

# 🌟 Example

Suppose:

| K | WCSS |
|----|------|
| 1 | 1000 |
| 2 | 600 |
| 3 | 300 |
| 4 | 250 |
| 5 | 220 |

If the graph bends at:

```text
K = 3
```

Then:

```text
Optimal Clusters = 3
```

---

# 📊 Applications of K-Means

- Customer Segmentation
- Student Segmentation
- Market Basket Analysis
- Recommendation Systems
- Image Segmentation
- Pattern Discovery
- Data Exploration

---

# ✅ Advantages of K-Means

- Easy to understand
- Simple implementation
- Fast training
- Works well on large datasets
- Efficient clustering algorithm

---

# ❌ Disadvantages of K-Means

- Need to choose K beforehand
- Sensitive to initial centroid placement
- Sensitive to outliers
- Struggles with irregular cluster shapes

---

# 🎓 Interview Questions

### What is K-Means?

K-Means is an unsupervised machine learning algorithm that partitions data into K clusters by assigning observations to the nearest centroid and repeatedly updating centroid locations.

---

### What is K in K-Means?

K represents the number of clusters.

---

### What is a Centroid?

A centroid is the center of a cluster and is calculated using the mean of observations within that cluster.

---

### What is WCSS?

WCSS (Within Cluster Sum of Squares) measures how close observations are to their cluster centroid.

---

### Why is WCSS important?

It helps evaluate clustering quality and is used in the Elbow Method.

---

### What is the Elbow Method?

The Elbow Method is used to determine the optimal number of clusters by plotting K versus WCSS and identifying the elbow point.

---

### When does K-Means stop?

K-Means stops when centroid positions no longer change significantly.

This is called convergence.

---

# 💻 Implementation Code

## Basic K-Means Clustering

```python
from sklearn.cluster import KMeans

kmeans = KMeans(
    n_clusters=3,
    random_state=42
)

kmeans.fit(X)

clusters = kmeans.labels_

print(clusters)
```

---

## Cluster Centroids

```python
print(kmeans.cluster_centers_)
```

---

## Elbow Method

```python
from sklearn.cluster import KMeans
import matplotlib.pyplot as plt

wcss = []

for k in range(1, 11):
    kmeans = KMeans(
        n_clusters=k,
        random_state=42
    )

    kmeans.fit(X)

    wcss.append(kmeans.inertia_)

plt.plot(range(1,11), wcss, marker='o')

plt.xlabel("Number of Clusters (K)")
plt.ylabel("WCSS")
plt.title("Elbow Method")

plt.show()
```

---

## Visualizing Clusters

```python
import matplotlib.pyplot as plt

kmeans = KMeans(
    n_clusters=3,
    random_state=42
)

y_kmeans = kmeans.fit_predict(X)

plt.scatter(
    X[:,0],
    X[:,1],
    c=y_kmeans,
    cmap='viridis'
)

plt.scatter(
    kmeans.cluster_centers_[:,0],
    kmeans.cluster_centers_[:,1],
    color='red',
    s=200,
    marker='X'
)

plt.show()
```

---

# 📌 Key Takeaways

✅ K-Means is an Unsupervised Learning algorithm.

✅ It performs clustering.

✅ K represents the number of clusters.

✅ Centroid represents the center of a cluster.

✅ K-Means repeatedly:
- Assigns observations
- Updates centroids

✅ WCSS measures cluster compactness.

✅ Smaller WCSS indicates better clustering.

✅ Elbow Method is used to determine the optimal K.

✅ K-Means stops when centroids stop moving.

---

# 🏁 Conclusion

K-Means is one of the most important clustering algorithms in Machine Learning. It automatically groups similar observations together without requiring labeled data.

By repeatedly assigning observations to the nearest centroid and updating centroid positions, K-Means discovers hidden patterns within data. The Elbow Method and WCSS help determine the optimal number of clusters, making K-Means a powerful tool for segmentation and exploratory data analysis.
``

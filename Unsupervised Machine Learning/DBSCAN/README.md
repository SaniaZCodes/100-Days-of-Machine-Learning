# 🔍 DBSCAN (Density-Based Spatial Clustering of Applications with Noise)

## 📌 Overview

DBSCAN is an Unsupervised Machine Learning clustering algorithm that groups data points based on density.

Unlike K-Means, DBSCAN does not require the number of clusters beforehand and can automatically identify outliers (noise points).

It is particularly useful when clusters have irregular shapes and when datasets contain noise or outliers.

---

# 🎯 Why DBSCAN?

K-Means has several limitations:

- Requires specifying K beforehand.
- Sensitive to outliers.
- Works best for spherical clusters.
- Struggles with irregular cluster shapes.

DBSCAN was introduced to overcome these limitations.

---

# 🧠 What is DBSCAN?

DBSCAN stands for:

```text
Density-Based Spatial Clustering
of Applications with Noise
```

It groups together observations that are densely packed and marks isolated observations as noise.

### Core Idea

```text
High Density
      ↓
Cluster

Low Density
      ↓
Noise
```

---

# 🔥 What is Density?

Density refers to the concentration of observations within a region.

### High Density Region

```text
● ● ● ●

● ● ● ●
```

Cluster ✅

---

### Low Density Region

```text
●


      ●


            ●
```

Not a cluster ❌

---

# ⚙️ Important Hyperparameters

DBSCAN uses two hyperparameters.

---

## 1. eps (Epsilon)

Represents:

```text
Radius Around a Point
```

Think of drawing a circle around a point.

Any observation inside this circle is considered a neighbor.

---

### Small eps

```text
Small Neighborhood
```

May create many clusters.

---

### Large eps

```text
Large Neighborhood
```

May merge clusters together.

---

## 2. min_samples

Represents:

```text
Minimum Number of Neighbors Required
```

to form a cluster.

---

Example:

```text
min_samples = 5
```

Meaning:

```text
At least 5 nearby points are required.
```

---

# 🎯 Types of Points in DBSCAN

DBSCAN classifies observations into three categories.

---

# 1️⃣ Core Point

A point that has at least:

```text
min_samples
```

neighbors inside:

```text
eps radius
```

Example:

```text
● ● ●

● C ●

● ● ●
```

Core Point ✅

---

# 2️⃣ Border Point

A point that does not satisfy:

```text
min_samples
```

but is connected to a Core Point.

Example:

```text
● ● ● ●

      B
```

Border Point ✅

---

# 3️⃣ Noise Point

A point that is neither:

- Core Point
- Border Point

Example:

```text
● ● ● ●


                    X
```

Noise Point ❌

---

# 🔄 How DBSCAN Works

## Step 1

Select:

```text
eps
```

and

```text
min_samples
```

---

## Step 2

Choose a point.

---

## Step 3

Check the number of neighbors within:

```text
eps radius
```

---

## Step 4

If neighbors ≥ min_samples

```text
Core Point
```

Create a cluster.

---

## Step 5

Expand the cluster by including neighboring points.

---

## Step 6

Repeat for remaining points.

---

## Step 7

Points that do not belong to any cluster become:

```text
Noise Points
```

---

# 🌟 Example

Suppose:

```text
eps = 2

min_samples = 4
```

DBSCAN checks:

```text
How many observations lie within distance 2?
```

If:

```text
Neighbors ≥ 4
```

Create cluster.

Otherwise continue searching.

---

# ⚔️ K-Means vs DBSCAN

| K-Means | DBSCAN |
|----------|---------|
| Requires K beforehand | No need for K |
| Uses Centroids | Uses Density |
| Sensitive to Outliers | Handles Outliers Naturally |
| Works best on spherical clusters | Handles irregular clusters |
| Uses WCSS and Elbow Method | Uses eps and min_samples |
| Every point belongs to a cluster | Noise points allowed |

---

# ⚔️ Hierarchical Clustering vs DBSCAN

| Hierarchical Clustering | DBSCAN |
|-------------------------|---------|
| Uses Dendrogram | Uses Density |
| Merges clusters progressively | Expands clusters through dense regions |
| Sensitive to noise | Handles noise naturally |
| Suitable for smaller datasets | Works well for noisy datasets |

---

# 📊 Applications of DBSCAN

- Customer Segmentation
- Fraud Detection
- Anomaly Detection
- Geographic Data Analysis
- Image Processing
- Noise Identification
- Social Network Analysis

---

# ✅ Advantages of DBSCAN

- No need to specify K.
- Handles outliers automatically.
- Discovers irregular cluster shapes.
- Works well on noisy datasets.
- Simple conceptual framework.

---

# ❌ Disadvantages of DBSCAN

- Performance depends on eps selection.
- Sensitive to min_samples value.
- Struggles when cluster densities vary significantly.
- Less effective in very high-dimensional datasets.

---

# 🎓 Interview Questions

### What is DBSCAN?

DBSCAN is a density-based clustering algorithm that groups observations based on density and identifies isolated observations as noise.

---

### What does DBSCAN stand for?

Density-Based Spatial Clustering of Applications with Noise.

---

### What are the two main hyperparameters in DBSCAN?

- eps
- min_samples

---

### What is a Core Point?

A point having at least min_samples neighbors inside the eps radius.

---

### What is a Border Point?

A point connected to a Core Point but not dense enough to become a Core Point itself.

---

### What is a Noise Point?

A point that does not belong to any cluster.

---

### Why is DBSCAN better than K-Means for outlier detection?

Because DBSCAN naturally labels isolated observations as noise points.

---

# 💻 Implementation Code

## Basic DBSCAN Clustering

```python
from sklearn.cluster import DBSCAN

dbscan = DBSCAN(
    eps=0.5,
    min_samples=5
)

clusters = dbscan.fit_predict(X)

print(clusters)
```

---

## Visualizing DBSCAN Clusters

```python
import matplotlib.pyplot as plt
from sklearn.cluster import DBSCAN

dbscan = DBSCAN(
    eps=0.5,
    min_samples=5
)

clusters = dbscan.fit_predict(X)

plt.scatter(
    X[:,0],
    X[:,1],
    c=clusters,
    cmap='rainbow'
)

plt.title("DBSCAN Clustering")

plt.show()
```

---

## Checking Cluster Labels

```python
print(set(clusters))
```

Example Output:

```text
{-1, 0, 1, 2}
```

Here:

```text
-1
```

represents:

```text
Noise Points
```

---

# 📌 Key Takeaways

✅ DBSCAN is an Unsupervised Learning algorithm.

✅ DBSCAN is Density-Based Clustering.

✅ No need to specify K.

✅ Uses:
- eps
- min_samples

✅ Three types of points:
- Core Point
- Border Point
- Noise Point

✅ Can identify outliers naturally.

✅ Handles irregular cluster shapes.

✅ Better than K-Means when noise and outliers are present.

---

# 🏁 Conclusion

DBSCAN is a powerful density-based clustering algorithm that identifies clusters based on densely populated regions within data. Unlike K-Means and Hierarchical Clustering, DBSCAN does not require specifying the number of clusters beforehand and can naturally detect outliers as noise points.

Its ability to discover irregular cluster shapes and handle noisy datasets makes it one of the most useful clustering algorithms in Unsupervised Learning.

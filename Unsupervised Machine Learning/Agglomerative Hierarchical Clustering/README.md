# 🌳 Agglomerative Hierarchical Clustering

## 📌 Overview

Agglomerative Hierarchical Clustering is an Unsupervised Machine Learning algorithm used to group similar observations into clusters.

Unlike K-Means, Hierarchical Clustering does not require specifying the number of clusters beforehand. Instead, it creates a hierarchy of clusters and allows us to decide the number of clusters later using a Dendrogram.

It follows a Bottom-Up approach where each observation starts as an individual cluster and the closest clusters are repeatedly merged.

---

# 🎯 What is Hierarchical Clustering?

Hierarchical Clustering is a clustering technique that builds a hierarchy (tree-like structure) of clusters.

The main goal is to group similar observations together based on their distance or similarity.

---

# 🌱 What Does Agglomerative Mean?

Agglomerative means:

```text
Bottom-Up Approach
```

The algorithm starts with:

```text
Each Observation = One Cluster
```

and repeatedly merges similar clusters until all observations belong to a single cluster.

---

# ⚙️ Working of Agglomerative Hierarchical Clustering

## Step 1: Start with Individual Clusters

Suppose we have:

```text
A
B
C
D
```

Initially:

```text
A

B

C

D
```

Each observation is its own cluster.

---

## Step 2: Find Closest Clusters

Suppose:

```text
A and B
```

are the closest observations.

Merge them:

```text
(A,B)

C

D
```

---

## Step 3: Find Next Closest Clusters

Suppose:

```text
C and D
```

are the closest.

Merge them:

```text
(A,B)

(C,D)
```

---

## Step 4: Merge Again

Finally:

```text
(A,B)

(C,D)
```

will merge into:

```text
(A,B,C,D)
```

---

## Step 5: Build Hierarchy

The algorithm creates a hierarchy of merges that can later be visualized using a Dendrogram.

---

# 🌳 What is a Dendrogram?

A Dendrogram is a tree-like diagram that shows how clusters are formed during Hierarchical Clustering.

Example:

```text
         --------
        /        \
      AB          CD
     /  \        /  \
    A    B      C    D
```

A Dendrogram helps us determine the optimal number of clusters.

---

# 🎯 Why Do We Need a Dendrogram?

Unlike K-Means, Hierarchical Clustering does not require:

```text
K = Number of Clusters
```

at the beginning.

Instead:

1. Build the hierarchy.
2. Plot the Dendrogram.
3. Decide where to cut the tree.
4. Obtain the desired number of clusters.

---

# 📊 Determining Number of Clusters

In Hierarchical Clustering, we look for the largest vertical distance in the Dendrogram.

A horizontal cut through this distance gives the optimal number of clusters.

This replaces the Elbow Method used in K-Means.

---

# 🔗 Linkage Methods

When merging clusters, the algorithm needs a way to measure distance between clusters.

These methods are called Linkage Methods.

---

## Single Linkage

Uses:

```text
Minimum Distance
```

between two clusters.

---

## Complete Linkage

Uses:

```text
Maximum Distance
```

between two clusters.

---

## Average Linkage

Uses:

```text
Average Distance
```

between clusters.

---

## Ward Linkage

Uses:

```text
Minimum Variance Increase
```

This is one of the most commonly used linkage methods.

---

# 🔄 Example

Suppose data contains:

```text
40

42

45

85

88

90
```

Hierarchical Clustering may build:

```text
(40,42)

(40,42,45)

(85,88)

(85,88,90)

((40,42,45),(85,88,90))
```

This entire merging process is shown in the dendrogram.

---

# 📊 Applications of Hierarchical Clustering

- Customer Segmentation
- Student Segmentation
- Market Research
- Gene Analysis
- Document Clustering
- Recommendation Systems

---

# ✅ Advantages of Hierarchical Clustering

- No need to specify K initially
- Easy visualization using Dendrogram
- Suitable for discovering hierarchical relationships
- Works well on small datasets
- Intuitive clustering process

---

# ❌ Disadvantages of Hierarchical Clustering

- Computationally expensive
- Slower on large datasets
- Sensitive to noise and outliers
- Difficult to scale on massive datasets

---

# ⚔️ K-Means vs Hierarchical Clustering

| K-Means | Hierarchical Clustering |
|----------|------------------------|
| Requires K before training | No need to specify K initially |
| Uses Centroids | Uses Cluster Merging |
| Uses WCSS | Uses Dendrogram |
| Uses Elbow Method | Uses Dendrogram for cluster selection |
| Fast and scalable | Slower and computationally expensive |
| Best for large datasets | Better for smaller datasets |
| Centroid-based clustering | Distance-based clustering |
| Clusters formed directly | Hierarchy formed first |

---

# 🎓 Interview Questions

### What is Hierarchical Clustering?

Hierarchical Clustering is an unsupervised learning technique that creates a hierarchy of clusters by repeatedly merging the most similar clusters.

---

### What is Agglomerative Clustering?

Agglomerative Clustering is the Bottom-Up version of Hierarchical Clustering where each observation starts as its own cluster and similar clusters are progressively merged.

---

### What is a Dendrogram?

A Dendrogram is a tree-like visualization that shows how clusters are merged during Hierarchical Clustering.

---

### Why is a Dendrogram important?

It helps determine the optimal number of clusters by analyzing cluster merge distances.

---

### What is the difference between K-Means and Hierarchical Clustering?

K-Means requires the number of clusters before training and uses centroids, whereas Hierarchical Clustering builds a cluster hierarchy first and uses a dendrogram to determine clusters.

---

# 💻 Implementation Code

## Plotting Dendrogram

```python
import scipy.cluster.hierarchy as sch
import matplotlib.pyplot as plt

plt.figure(figsize=(10,5))

dendrogram = sch.dendrogram(
    sch.linkage(
        X,
        method='ward'
    )
)

plt.title("Dendrogram")
plt.xlabel("Data Points")
plt.ylabel("Euclidean Distance")

plt.show()
```

---

## Agglomerative Hierarchical Clustering

```python
from sklearn.cluster import AgglomerativeClustering

hc = AgglomerativeClustering(
    n_clusters=3,
    linkage='ward'
)

clusters = hc.fit_predict(X)

print(clusters)
```

---

## Visualizing Clusters

```python
import matplotlib.pyplot as plt

plt.scatter(
    X[:,0],
    X[:,1],
    c=clusters,
    cmap='rainbow'
)

plt.title("Hierarchical Clustering")
plt.show()
```

---

# 📌 Key Takeaways

✅ Hierarchical Clustering is an Unsupervised Learning algorithm.

✅ Agglomerative Clustering follows a Bottom-Up approach.

✅ Every observation initially forms its own cluster.

✅ Similar clusters are repeatedly merged.

✅ Dendrogram visualizes the clustering hierarchy.

✅ Dendrogram helps determine the number of clusters.

✅ Unlike K-Means, no initial K value is required.

✅ Common linkage methods:
- Single Linkage
- Complete Linkage
- Average Linkage
- Ward Linkage

✅ Best suited for smaller datasets.

---

# 🏁 Conclusion

Agglomerative Hierarchical Clustering is a powerful clustering algorithm that builds a hierarchy of clusters by repeatedly merging similar observations.

Unlike K-Means, it does not require the number of clusters beforehand and uses a Dendrogram to visualize cluster formation and determine the optimal number of clusters.

Its intuitive clustering process and ability to reveal hierarchical relationships make it a valuable tool in exploratory data analysis and pattern discovery.

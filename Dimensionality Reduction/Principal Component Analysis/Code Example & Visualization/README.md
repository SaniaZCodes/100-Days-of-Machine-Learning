# PCA Part 3 - Code Example & Visualization 📊

## What is PCA?

PCA (Principal Component Analysis) is a dimensionality reduction technique.

It reduces the number of features while preserving maximum information.

---

## Why PCA?

To solve the Curse of Dimensionality.

Problems:

- Too many features
- Noise
- Overfitting
- Slow training

---

## PCA Workflow

Step 1

Standardize the data.

---

Step 2

Find directions with maximum variance.

---

Step 3

Create Principal Components (PC1, PC2, ...)

---

Step 4

Keep important components.

---

Step 5

Reduce dimensions.

---

## Standardization

PCA is sensitive to feature scales.

Always standardize before applying PCA.

### Code

```python
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()

X_scaled = scaler.fit_transform(X)
```

---

## Apply PCA

```python
from sklearn.decomposition import PCA

pca = PCA(n_components=2)

X_pca = pca.fit_transform(X_scaled)
```

---

## n_components

Determines how many principal components to keep.

### Example

```python
PCA(n_components=2)
```

Keep 2 Principal Components.

---

## Explained Variance Ratio

```python
pca.explained_variance_ratio_
```

Example:

```python
[0.95, 0.04]
```

Meaning:

PC1 → 95% Information

PC2 → 4% Information

Total Information Preserved:

99%

---

## Eigenvalues

In PCA:

Eigenvalue = Amount of Variance (Information)

---

### Easy Memory

Eigenvalue

↓

How Much Information?

---

### Example

```python
pca.explained_variance_ratio_
```

Output:

```python
[0.0578, 0.0414, 0.0380]
```

Meaning:

PC1 contains 5.78% variance

PC2 contains 4.14% variance

PC3 contains 3.80% variance

---

## Eigenvectors (PCA Components)

```python
pca.components_
```

These represent the directions of the principal components.

They show how original features contribute to each principal component.

---

### Easy Memory

Eigenvector

↓

Direction

---

## Important Difference

Eigenvector

↓

Where is the information?

(Direction)

---

Eigenvalue

↓

How much information is there?

(Variance)

---

## PCA Creates New Features

Before PCA:

Age

Salary

Experience

---

After PCA:

PC1

PC2

PC3

---

PCA does not select existing features.

PCA creates new features.

---

## Complete Code

```python
from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import PCA

# Scale Data
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

# Apply PCA
pca = PCA(n_components=2)

X_pca = pca.fit_transform(X_scaled)

# Explained Variance
print(pca.explained_variance_ratio_)

# Components (Eigenvectors)
print(pca.components_)
```

---

## Interview Point 🎯

PC1 contains the maximum variance.

PC2 contains the second highest variance.

PCA keeps components with maximum variance and removes less informative components.

---

## Memory Trick 🧠

Curse of Dimensionality

↓

Problem

---

PCA

↓

Solution

---

Variance

↓

Information

---

PC1

↓

Most Information

---

Eigenvector

↓

Direction

---

Eigenvalue

↓

Amount of Information

---

## Golden Line 🌟

PCA transforms original features into principal components and preserves maximum variance while reducing dimensionality.

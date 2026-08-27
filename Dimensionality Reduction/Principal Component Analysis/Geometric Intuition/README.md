# PCA Part 1 - Geometric Intuition 📊

## What is PCA?

PCA (Principal Component Analysis) is a dimensionality reduction technique.

Its goal is to reduce the number of features while preserving as much information as possible.

---

## Why PCA?

To solve the Curse of Dimensionality.

Problems:

- Too many features
- Noise
- Overfitting
- Slow training

---

## Key Idea

Keep the most informative directions in the data and remove less important directions.

---

## Principal Components

### PC1

First Principal Component

Contains maximum variance.

---

### PC2

Second Principal Component

Contains the next highest variance.

---

## Variance

Variance measures how spread out the data is.

PCA assumes:

Higher Variance
↓
More Information

---

## Before PCA

X-axis + Y-axis

↓

2 Dimensions

---

## After PCA

PC1

↓

1 Dimension

---

## Important Point

PCA creates new features.

It does not simply select existing features.

---

## Golden Line 🌟

PCA reduces dimensions by keeping directions with maximum variance and removing less informative directions.

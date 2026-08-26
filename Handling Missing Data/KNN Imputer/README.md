# KNN Imputer 🧠

## What?

KNN Imputer fills missing values using similar records.

---

## How?

1. Find nearest neighbors.
2. Check their values.
3. Fill missing value using those neighbors.

---

## Example

Age = 22

Nearest Ages:

21 → Salary = 32000

23 → Salary = 34000

↓

Missing Salary ≈ 33000

---

## Code

```python
from sklearn.impute import KNNImputer

imputer = KNNImputer(n_neighbors=5)

X_train = imputer.fit_transform(X_train)
X_test = imputer.transform(X_test)
```

---

## Advantages

✅ Smart Imputation

✅ Uses nearby records

✅ Better than mean/median

---

## Golden Line 🌟

KNN Imputer fills missing values using the most similar records in the dataset.

---

## Types of Weights

1. uniform   give equal importance to all neighbors
2. distance  give more importance to the closet one neighbor

---

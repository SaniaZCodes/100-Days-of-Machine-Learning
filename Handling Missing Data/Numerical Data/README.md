# Simple Imputer (Numerical Data) 🧩

## What?

Used to fill missing numerical values instead of deleting rows.

---

## Why?

✅ Prevent data loss

✅ Keep more records

✅ Simple and fast

---

## Mean Imputation

Replace missing values with mean.

```python
SimpleImputer(strategy='mean')
```

---

## Median Imputation

Replace missing values with median.

Best when outliers exist.

```python
SimpleImputer(strategy='median')
```

---

## Constant Imputation

Replace missing values with a fixed value.

```python
SimpleImputer(
    strategy='constant',
    fill_value=0
)
```

---

## Code

```python
from sklearn.impute import SimpleImputer

imputer = SimpleImputer(strategy='mean')

X_train = imputer.fit_transform(X_train)
X_test = imputer.transform(X_test)
```

---

## Key Rule

Fit only on training data.

---

## Golden Line 🌟

Simple Imputer fills missing values instead of removing data.
`

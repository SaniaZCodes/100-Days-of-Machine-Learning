# Missing Categorical Data 🧩

## What?

Used to handle missing values in categorical columns.

---

## Most Frequent Imputation

Replace missing values with the most common category.

Example:

Male
Female
Male
NaN

↓

Male
Female
Male
Male

### Code

```python
from sklearn.impute import SimpleImputer

imputer = SimpleImputer(strategy='most_frequent')
```

---

## Missing Category Imputation

Create a new category called "Missing".

Example:

Male
Female
NaN

↓

Male
Female
Missing

### Code

```python
imputer = SimpleImputer(
    strategy='constant',
    fill_value='Missing'
)
```

---

## Golden Line 🌟

For categorical data, fill missing values with the most frequent category or create a new "Missing" category.

# Column Transformer 🔄

## What?

Column Transformer is used when different columns need different preprocessing techniques.

---

## Example

Numerical Columns:

- Age
- Salary

Apply:

StandardScaler

---

Categorical Columns:

- Gender
- City

Apply:

OneHotEncoder

---

## Why?

Different columns require different preprocessing.

Column Transformer helps us apply everything in one step.

---

## Benefits

✅ Clean code

✅ Easy preprocessing

✅ Useful in real projects

✅ Works well with pipelines

---

## Code

```python
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import OneHotEncoder, StandardScaler

transformer = ColumnTransformer(
    transformers=[
        ('num', StandardScaler(), ['Age','Salary']),
        ('cat', OneHotEncoder(), ['Gender','City'])
    ]
)
```

---

## Golden Line 🌟

Different columns can have different transformations.
Column Transformer manages them all in one place.

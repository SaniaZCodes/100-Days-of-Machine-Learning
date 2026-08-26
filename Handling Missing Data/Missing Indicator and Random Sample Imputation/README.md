# Missing Indicator & Random Sample Imputation 📊

## Missing Indicator

Creates a new column that shows whether a value was missing.

0 = Not Missing

1 = Missing

### Example

Age   Age_Missing

20         0

NaN        1

25         0

---

## Code

```python
from sklearn.impute import MissingIndicator

mi = MissingIndicator()
```

---

## Random Sample Imputation

Replaces missing values using random values from the same column.

### Example

20
25
30
35
NaN

↓

20
25
30
35
25

---

## Why?

✅ Preserves data distribution

✅ Better than mean/median in some cases

---

## Golden Line 🌟

Missing Indicator tells the model which values were missing, while Random Sample Imputation fills missing values using existing observations.

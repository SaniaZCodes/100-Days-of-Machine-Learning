# Binning & Binarization 📊

## What is Discretization?

Converting continuous numerical data into categories/groups.

Example:

Age

18
25
40
60

↓

Young
Adult
Senior

---

## What is Binning?

A type of discretization used to divide numerical data into groups (bins).

---

## Equal Width Binning

All bins have equal width.

Example:

0-25

25-50

50-75

75-100

### Code

```python
pd.cut(df['Age'], bins=4)
```

---

## Quantile Binning

Each bin contains approximately the same number of records.

### Code

```python
pd.qcut(df['Age'], q=4)
```

---

## K-Means Binning

Uses KMeans clustering to create bins automatically.

Used less frequently than Equal Width and Quantile Binning.

---

## Why Use Binning?

✅ Reduce Noise

✅ Handle Outliers

✅ Create Meaningful Groups

✅ Simplify Data

---

## What is Binarization?

Convert values into only:

0 or 1

---

## Example

Marks:

20
40
60
80

Threshold = 50

↓

0
0
1
1

---

## Code

```python
from sklearn.preprocessing import Binarizer

binarizer = Binarizer(threshold=50)
```

---

## Difference

Discretization
↓
Many categories

Example:
Young, Adult, Senior

---

Binarization
↓
Only two categories

Example:
0 and 1

---

## Golden Line 🌟

Discretization converts numbers into groups, while Binarization converts values into only 0 and 1.

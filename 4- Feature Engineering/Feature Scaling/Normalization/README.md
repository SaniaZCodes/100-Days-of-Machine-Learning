# Normalization 📊

## What?

Normalization scales data to a fixed range.

Most common range:

0 to 1

---

## Why?

✅ Makes features comparable

✅ Prevents large values from dominating

✅ Helps many ML algorithms

---

## MinMax Scaling

Formula:

(X - Min) / (Max - Min)

Output:

0 to 1

---

## MaxAbs Scaling

Formula:

X / Maximum Absolute Value

Output:

-1 to 1

---

## Robust Scaling

Uses:

- Median
- IQR

Best when outliers exist.

---

## Difference from Standardization

Standardization:
Mean = 0
Std = 1

Normalization:
Values between 0 and 1

---

## Golden Line 🌟

Normalization changes the range of data, not its meaning.

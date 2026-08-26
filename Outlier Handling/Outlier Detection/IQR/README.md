# Outlier Detection and Removal Using IQR Method 📊

## What is IQR?

IQR (Inter Quartile Range) measures the spread of the middle 50% of the data.

Formula:

IQR = Q3 - Q1

---

## Quartiles

Q1 = 25th Percentile

Q2 = Median (50th Percentile)

Q3 = 75th Percentile

---

## Outlier Detection Rule

Lower Bound:

Q1 - 1.5 × IQR

Upper Bound:

Q3 + 1.5 × IQR

---

## Outlier Condition

Value < Lower Bound

or

Value > Upper Bound

↓

Outlier

---

## Code

```python
Q1 = df['Age'].quantile(0.25)
Q3 = df['Age'].quantile(0.75)

IQR = Q3 - Q1

lower_bound = Q1 - 1.5 * IQR
upper_bound = Q3 + 1.5 * IQR
```

---

## Detect Outliers

```python
outliers = df[
    (df['Age'] < lower_bound) |
    (df['Age'] > upper_bound)
]
```

---

## Remove Outliers

```python
df = df[
    (df['Age'] >= lower_bound) &
    (df['Age'] <= upper_bound)
]
```

---

## Advantages

✅ Works on skewed data

✅ Robust to outliers

✅ No normality assumption

---

## Golden Line 🌟

IQR detects outliers using quartiles instead of mean and standard deviation, making it suitable for skewed datasets.

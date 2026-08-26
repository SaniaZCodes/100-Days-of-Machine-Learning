# Outlier Detection and Removal Using Z-Score Method 📊

## What is Z-Score?

Z-Score measures how many standard deviations a value is away from the mean.

It is used to detect outliers in approximately normal distributions.

---

## Formula

Z = (X - Mean) / Standard Deviation

Where:

X = Current Value

Mean = Average of the column

Standard Deviation = Spread of the data

---

## What is Mean?

Mean tells us the center of the data.

---

## What is Standard Deviation?

Standard Deviation tells us how far data points are spread from the mean.

---

## Z-Score Rule

Z > 3

→ Outlier

Z < -3

→ Outlier

---

## Why ±3?

In a normal distribution, most values lie between:

-3 and +3

Values outside this range are considered unusual.

---

## When To Use?

✅ Data is approximately normally distributed.

Check skewness first.

```python
df['column_name'].skew()
```

Normal Range:

-0.5 to +0.5

---

## Detect Outliers

```python
from scipy import stats

z_scores = stats.zscore(df['Age'])

outliers = df[(z_scores > 3) | (z_scores < -3)]
```

---

## Remove Outliers

```python
df = df[(z_scores >= -3) & (z_scores <= 3)]
```

---

## Advantages

✅ Easy

✅ Fast

✅ Simple Mathematical Method

---

## Disadvantages

❌ Not suitable for highly skewed data

❌ Sensitive to extreme values

---

## Interview Point 🎯

Mean tells us where the center of the data is, while Standard Deviation tells us how far the data is spread around that center.

---

## Golden Line 🌟

A value with a Z-Score greater than 3 or less than -3 is usually considered an outlier.

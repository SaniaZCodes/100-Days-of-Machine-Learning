# What Are Outliers? 📊

## What?

Outliers are values that are significantly different from the majority of the data.

---

## Example

Age

20

21

22

23

24

500

Here:

500 = Outlier

Because it is far away from the other values.

---

## Why Are Outliers Important?

✅ Can affect Mean

✅ Can affect Model Performance

✅ Can produce misleading results

✅ Can distort data distribution

---

## Causes of Outliers

- Data Entry Error
- Measurement Error
- Genuine Extreme Value

---

## How To Detect Outliers?

### Visual Methods

✅ Boxplot

✅ Histogram

---

### Statistical Methods

✅ Z-Score Method

✅ IQR Method

✅ Percentile Method

---

## Boxplot Code

```python
import seaborn as sns

sns.boxplot(df['Age'])
```

---

## Skewness Code

```python
df['Age'].skew()
```

---

## Skewness Interpretation

-0.5 to +0.5
→ Approximately Normal

0.5 to 1
→ Moderately Skewed

Greater than 1
→ Highly Skewed

---

## Interview Point 🎯

A boxplot identifies outliers as points lying outside the whiskers, while skewness measures the asymmetry of the distribution.

Positive skew indicates a longer right tail.

Negative skew indicates a longer left tail.

---

## Quick Memory

Missing Value
↓
Data Absent

Outlier
↓
Data Present But Unusual

---

## Golden Line 🌟

Outliers are unusual observations that are far away from the majority of the data and may negatively impact analysis and machine learning models.

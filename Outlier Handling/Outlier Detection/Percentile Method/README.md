# Outlier Detection and Removal Using Percentile Method 📊

## What is Percentile Method?

Percentile Method identifies outliers using percentile values.

It assumes that extremely small and extremely large values are potential outliers.

---

## Common Percentile Thresholds

1st Percentile (0.01)

99th Percentile (0.99)

or

5th Percentile (0.05)

95th Percentile (0.95)

---

## Idea

Values below the lower percentile or above the upper percentile are considered outliers.

---

## Example

Data:

10

20

30

40

50

60

70

80

90

1000

Here:

1000 is an extreme value.

It may fall above the 99th percentile and be considered an outlier.

---

## Calculate Percentile Limits

```python
lower_limit = df['Age'].quantile(0.01)

upper_limit = df['Age'].quantile(0.99)
```

---

## Outlier Detection Rule

Value < Lower Limit

OR

Value > Upper Limit

↓

Outlier

---

## Detect Outliers

```python
outliers = df[
    (df['Age'] < lower_limit) |
    (df['Age'] > upper_limit)
]
```

---

## Remove Outliers

```python
df = df[
    (df['Age'] >= lower_limit) &
    (df['Age'] <= upper_limit)
]
```

---

## Advantages

✅ Easy to Understand

✅ Easy to Implement

✅ Works Well for Extreme Values

✅ No Need for Normal Distribution

---

## Disadvantages

❌ Choice of percentile is subjective

❌ Genuine values may be removed

❌ Different percentile thresholds give different results

---

## Interview Point 🎯

Percentile Method identifies outliers by defining lower and upper percentile boundaries and treating values outside those boundaries as outliers.

---

## Memory Trick 🧠

1% Percentile
↓
Lower Limit

99% Percentile
↓
Upper Limit

Outside Limits
↓
Outlier

---

## Golden Line 🌟

Percentile Method detects outliers using percentile thresholds instead of mean, standard deviation, or quartiles.

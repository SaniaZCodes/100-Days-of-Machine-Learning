# Percentile Winsorization 📊

## What?

Extreme values are capped using percentile limits.

---

## Common Limits

1st Percentile

99th Percentile

or

5th Percentile

95th Percentile

---

## Formula

Lower Limit:

1st Percentile

---

Upper Limit:

99th Percentile

---

## Outlier Rule

Value > Upper Limit

↓

Replace with Upper Limit

---

Value < Lower Limit

↓

Replace with Lower Limit

---

## Example

Lower Limit = 20

Upper Limit = 100

---

Before

10

25

50

500

---

After

20

25

50

100

---

## Code

```python
lower_limit = df['Age'].quantile(0.01)
upper_limit = df['Age'].quantile(0.99)

df['Age'] = df['Age'].clip(
    lower=lower_limit,
    upper=upper_limit
)
```

---

## Golden Line 🌟

Percentile Winsorization caps extreme values at percentile boundaries instead of deleting them.

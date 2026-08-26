# Z-Score Winsorization 📊

## What?

Instead of removing outliers, extreme values are capped using Z-Score limits.

---

## Formula

Upper Limit:

Mean + 3 × Standard Deviation

Lower Limit:

Mean - 3 × Standard Deviation

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

Mean = 50

Standard Deviation = 10

Upper Limit:

50 + 3(10)

= 80

Lower Limit:

50 - 3(10)

= 20

---

Before

20

30

40

100

---

After

20

30

40

80

---

## Code

```python
mean = df['Age'].mean()
std = df['Age'].std()

upper_limit = mean + 3 * std
lower_limit = mean - 3 * std

df['Age'] = np.where(
    df['Age'] > upper_limit,
    upper_limit,
    np.where(
        df['Age'] < lower_limit,
        lower_limit,
        df['Age']
    )
)
```

---

## Golden Line 🌟

Z-Score Winsorization caps values using Mean ± 3 × Standard Deviation instead of removing them.

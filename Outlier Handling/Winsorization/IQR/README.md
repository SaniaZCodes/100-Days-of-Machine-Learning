# IQR Winsorization 📊

## What?

Instead of removing outliers, extreme values are capped using IQR boundaries.

---

## Formula

IQR = Q3 - Q1

---

Upper Limit:

Q3 + 1.5 × IQR

---

Lower Limit:

Q1 - 1.5 × IQR

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

Q1 = 30

Q3 = 70

IQR = 40

Upper Limit:

70 + 1.5(40)

= 130

Lower Limit:

30 - 1.5(40)

= -30

---

Before

20

30

50

500

---

After

20

30

50

130

---

## Code

```python
Q1 = df['Age'].quantile(0.25)
Q3 = df['Age'].quantile(0.75)

IQR = Q3 - Q1

lower_limit = Q1 - 1.5 * IQR
upper_limit = Q3 + 1.5 * IQR

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

IQR Winsorization caps values using quartile-based boundaries rather than removing observations.

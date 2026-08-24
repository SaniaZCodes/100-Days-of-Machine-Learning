# Complete Case Analysis

## What?

Remove rows that contain missing values.

## When to Use?

✅ Missing values are very few.

✅ Enough data is available.

## Code

```python
df = df.dropna()
```

## Disadvantage

May remove a large amount of data.

## Golden Line 🌟

Complete Case Analysis removes rows with missing values instead of filling them.

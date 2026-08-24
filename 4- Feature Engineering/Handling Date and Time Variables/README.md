# Handling Date and Time Variables 📅

## What?

Convert date and time columns into meaningful features for Machine Learning.

---

## Why?

Machine Learning models cannot directly understand dates.

Useful features need to be extracted.

---

## Features Extracted

✅ Year

✅ Month

✅ Day

✅ Day of Week

✅ Hour

✅ Minute

✅ Time Difference

---

## Convert to Datetime

```python
df['Date'] = pd.to_datetime(df['Date'])
```

---

## Extract Year

```python
df['Year'] = df['Date'].dt.year
```

---

## Extract Month

```python
df['Month'] = df['Date'].dt.month
```

---

## Extract Day

```python
df['Day'] = df['Date'].dt.day
```

---

## Example

Date of Birth

15-08-2004

↓

Age = 22

---

## Golden Line 🌟

Date columns are rarely useful directly. Extract meaningful features from them.

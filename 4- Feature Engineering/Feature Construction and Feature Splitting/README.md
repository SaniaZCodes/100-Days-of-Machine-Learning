# Feature Construction & Feature Splitting 🔧

## Feature Construction

Create a new feature using existing features.

### Examples

Selling Price - Purchase Price

↓

Profit

---

Date of Birth

↓

Age

---

## Code

```python
df['Profit'] = (
    df['Selling_Price']
    - df['Purchase_Price']
)
```

---

## Feature Splitting

Split one feature into multiple features.

### Examples

Full Name

↓

First Name + Last Name

---

Date

↓

Day + Month + Year

---

## Code

```python
df[['First_Name','Last_Name']] = (
    df['Name'].str.split(
        " ",
        expand=True
    )
)
```

---

## Difference

Feature Construction

↓

Creates New Features

---

Feature Splitting

↓

Breaks One Feature Into Multiple Features

---

## Golden Line 🌟

Feature Construction creates new information, while Feature Splitting extracts information from an existing feature.

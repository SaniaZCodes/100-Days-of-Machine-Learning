# Machine Learning Pipeline 🚀

## What?

A Pipeline combines multiple preprocessing and modeling steps into a single workflow.

---

## Why?

✅ Cleaner code

✅ Less mistakes

✅ Easy training

✅ Easy deployment

---

## Workflow

Data
 ↓
Encoding
 ↓
Scaling
 ↓
Model
 ↓
Prediction

---

## Code

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression

pipe = Pipeline([
    ('scaler', StandardScaler()),
    ('model', LogisticRegression())
])
```

---

## Use With

- StandardScaler
- OneHotEncoder
- ColumnTransformer
- Regression Models
- Classification Models

---

## Golden Line 🌟

Pipeline automates preprocessing and model training in a single workflow.

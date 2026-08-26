# MICE (Iterative Imputer) 🧠

## What?

MICE fills missing values by predicting them using other features in the dataset.

---

## How Does It Work?

Step 1:
Fill missing values with an initial guess (usually mean).

Step 2:
Build a model using other columns.

Step 3:
Predict a better value.

Step 4:
Replace the old guess.

Step 5:
Repeat the process until the values become stable.

---

## Example

Before:

Age    Salary

20     30000

25     40000

30     NaN

35     60000

---

Initial Guess:

Salary = 43333

---

Model Prediction:

Salary = 50000

---

Final Value:

Salary = 50000

---

## Why Use It?

✅ Uses relationships between columns

✅ More intelligent than mean imputation

✅ Better estimates

---

## Code

```python
from sklearn.experimental import enable_iterative_imputer
from sklearn.impute import IterativeImputer

imputer = IterativeImputer()

X_train = imputer.fit_transform(X_train)
X_test = imputer.transform(X_test)
```

---

## Important Point

fit()
↓
Learns relationships between features

transform()
↓
Predicts and fills missing values

---

## Comparison

Mean Imputer
↓
Use Average

KNN Imputer
↓
Use Similar Rows

MICE Imputer
↓
Build Model and Predict

---

## Golden Line 🌟

MICE predicts missing values using other features and keeps improving the prediction through multiple iterations.

----

## Golden Interview Answer 🌟

IterativeImputer uses Bayesian Ridge Regression by default. We can provide another estimator such as Random Forest if we believe the relationships between features are complex. In practice, different estimators are often tested and the one giving the best results is selected.

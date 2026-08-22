# Standardization 📊

## What?

Standardization is a feature scaling technique used to bring numerical features to a common scale.

---

## Why Do We Need It?

Suppose:

Age = 20, 25, 30

Salary = 20000, 50000, 80000

Salary values are much bigger than Age values.

Some algorithms may think Salary is more important just because the numbers are larger.

Standardization solves this problem.

---

## Formula

Z = (X - Mean) / Standard Deviation

Where:

X = Original Value

Mean = Average of the feature

Standard Deviation = Spread of the feature

---

## After Standardization

Mean = 0

Standard Deviation = 1

---

## Example

Original Values:

20, 25, 30

Standardized Values:

-1.22, 0, 1.22

---

## Algorithms That Need It

✅ KNN

✅ SVM

✅ Logistic Regression

✅ Linear Regression (Gradient Descent)

✅ PCA

---

## Algorithms That Usually Don't Need It

✅ Decision Tree

✅ Random Forest

✅ XGBoost

---

## Key Idea

Standardization does NOT change the meaning of data.

It only changes the scale of data.

---

## Golden Line 🌟

Standardization centers data around zero and scales it using standard deviation.

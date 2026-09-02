# Classification Metrics

# Overview

After training a Classification Model, the next step is evaluating its performance.

Unlike Regression, where metrics such as MAE, MSE, RMSE, and R² Score are used, Classification models require different evaluation techniques.

Classification Metrics help us understand:

- How accurate the model is.
- What types of mistakes the model makes.
- How well the model identifies positive classes.
- Whether the model performs well on imbalanced datasets.

---

# Why Classification Metrics?

Suppose a model predicts:

```text
Pass / Fail

Spam / Not Spam

Disease / No Disease
```

Simply checking predictions is not enough.

We need proper evaluation metrics to determine whether the model is reliable.

---

# Accuracy

Accuracy is the simplest Classification Metric.

It measures the percentage of correct predictions made by the model.

---

## Formula

```text
Accuracy

=

Correct Predictions
------------------
Total Predictions
```

---

## Example

Actual Values

```text
1 0 1 1 0
```

Predicted Values

```text
1 0 1 0 0
```

Correct Predictions:

```text
4
```

Total Predictions:

```text
5
```

Accuracy:

```text
4 / 5

=

80%
```

---

## sklearn Implementation

```python
from sklearn.metrics import accuracy_score

accuracy = accuracy_score(y_test, y_pred)

print("Accuracy:", accuracy)
```

---

# Limitation of Accuracy

Accuracy becomes misleading when the dataset is imbalanced.

---

## Example

Dataset:

```text
95 Healthy People

5 Diseased People
```

Model Prediction:

```text
Everyone Healthy
```

Accuracy:

```text
95%
```

Even though the model failed to identify a single diseased patient.

Therefore, Accuracy alone should not be used for evaluating imbalanced datasets.

---

# Confusion Matrix

A Confusion Matrix provides a detailed view of model predictions.

It shows:

```text
Correct Predictions

Incorrect Predictions

Types of Errors
```

---

# Confusion Matrix Structure

```text
                    Predicted

                 Negative   Positive

Actual Negative     TN         FP

Actual Positive     FN         TP
```

---

# True Positive (TP)

Actual:

```text
Positive
```

Predicted:

```text
Positive
```

Correct Positive Prediction.

Example:

```text
Diseased Person
↓
Predicted Diseased
```

---

# True Negative (TN)

Actual:

```text
Negative
```

Predicted:

```text
Negative
```

Correct Negative Prediction.

Example:

```text
Healthy Person
↓
Predicted Healthy
```

---

# False Positive (FP)

Actual:

```text
Negative
```

Predicted:

```text
Positive
```

Incorrect Positive Prediction.

Example:

```text
Healthy Person
↓
Predicted Diseased
```

Also known as:

```text
Type 1 Error
```

---

# False Negative (FN)

Actual:

```text
Positive
```

Predicted:

```text
Negative
```

Incorrect Negative Prediction.

Example:

```text
Diseased Person
↓
Predicted Healthy
```

Also known as:

```text
Type 2 Error
```

---

# sklearn Implementation

```python
from sklearn.metrics import confusion_matrix

cm = confusion_matrix(y_test, y_pred)

print(cm)
```

---

# Visualizing Confusion Matrix

```python
from sklearn.metrics import ConfusionMatrixDisplay
import matplotlib.pyplot as plt

ConfusionMatrixDisplay.from_predictions(
    y_test,
    y_pred
)

plt.show()
```

---

# Type 1 Error

```text
False Positive
```

Actual:

```text
No
```

Predicted:

```text
Yes
```

Example:

```text
Healthy Person
↓
Predicted Diseased
```

False Alarm.

---

# Type 2 Error

```text
False Negative
```

Actual:

```text
Yes
```

Predicted:

```text
No
```

Example:

```text
Diseased Person
↓
Predicted Healthy
```

Missed Detection.

---

# Precision

Precision measures how many positive predictions are actually positive.

---

## Formula

```text
Precision

=

TP
----------
TP + FP
```

---

## Interpretation

Precision answers:

```text
Out of all predicted positives,
how many were actually positive?
```

---

## Example

```text
TP = 80

FP = 20
```

Precision:

```text
80 / (80 + 20)

=

80%
```

---

## When Precision Matters

- Spam Detection
- Recommendation Systems
- Email Filtering

When False Positives are costly.

---

## sklearn Implementation

```python
from sklearn.metrics import precision_score

precision = precision_score(
    y_test,
    y_pred
)

print("Precision:", precision)
```

---

# Recall

Recall measures how many actual positives were correctly identified.

---

## Formula

```text
Recall

=

TP
----------
TP + FN
```

---

## Interpretation

Recall answers:

```text
Out of all actual positives,
how many did we correctly find?
```

---

## Example

```text
TP = 80

FN = 20
```

Recall:

```text
80 / (80 + 20)

=

80%
```

---

## When Recall Matters

- Disease Detection
- Fraud Detection
- Security Systems

When missing a positive case is dangerous.

---

## sklearn Implementation

```python
from sklearn.metrics import recall_score

recall = recall_score(
    y_test,
    y_pred
)

print("Recall:", recall)
```

---

# Precision vs Recall

## Precision

Focuses on:

```text
Predicted Positives
```

Question:

```text
How many positive predictions were correct?
```

---

## Recall

Focuses on:

```text
Actual Positives
```

Question:

```text
How many actual positives were found?
```

---

# F1 Score

F1 Score combines Precision and Recall into a single metric.

It is useful when both False Positives and False Negatives matter.

---

## Formula

```text
F1 Score

=

2 × Precision × Recall
-----------------------
Precision + Recall
```

---

## Interpretation

High F1 Score indicates:

✅ High Precision

✅ High Recall

---

## sklearn Implementation

```python
from sklearn.metrics import f1_score

f1 = f1_score(
    y_test,
    y_pred
)

print("F1 Score:", f1)
```

---

# ROC Curve

ROC stands for:

```text
Receiver Operating Characteristic
```

It evaluates model performance at different classification thresholds.

---

# Important Components

## True Positive Rate (TPR)

Also known as:

```text
Recall
```

Formula:

```text
TP
----------
TP + FN
```

---

## False Positive Rate (FPR)

Formula:

```text
FP
----------
FP + TN
```

---

# ROC Curve Axes

## X-Axis

```text
False Positive Rate (FPR)
```

---

## Y-Axis

```text
True Positive Rate (TPR)
```

---

# Purpose

ROC Curve shows how model performance changes when the threshold changes.

---

# ROC Curve Code

```python
from sklearn.metrics import roc_curve
import matplotlib.pyplot as plt

y_prob = model.predict_proba(X_test)[:, 1]

fpr, tpr, thresholds = roc_curve(
    y_test,
    y_prob
)

plt.plot(fpr, tpr)
plt.xlabel("False Positive Rate")
plt.ylabel("True Positive Rate")
plt.title("ROC Curve")
plt.show()
```

---

# ROC-AUC

AUC means:

```text
Area Under Curve
```

It summarizes the ROC Curve into a single value.

---

# Range

```text
0 to 1
```

---

# Interpretation

## AUC = 1.0

```text
Perfect Classifier
```

---

## AUC = 0.9

```text
Excellent Classifier
```

---

## AUC = 0.8

```text
Good Classifier
```

---

## AUC = 0.5

```text
Random Guessing
```

---

# sklearn Implementation

```python
from sklearn.metrics import roc_auc_score

y_prob = model.predict_proba(X_test)[:, 1]

auc = roc_auc_score(
    y_test,
    y_prob
)

print("ROC-AUC:", auc)
```

---

# Complete Classification Report

Instead of calculating metrics individually:

```python
from sklearn.metrics import classification_report

print(
    classification_report(
        y_test,
        y_pred
    )
)
```

Output Includes:

- Precision
- Recall
- F1 Score
- Support

---

# Summary of Metrics

## Accuracy

Measures overall correctness.

---

## Confusion Matrix

Shows prediction details and types of errors.

---

## Precision

Measures correctness of positive predictions.

---

## Recall

Measures ability to find positive cases.

---

## F1 Score

Balances Precision and Recall.

---

## ROC-AUC

Measures model's ability to distinguish between classes across different thresholds.

---

# Interview Questions

## What is Accuracy?

Accuracy is the ratio of correct predictions to total predictions.

---

## Why is Accuracy not reliable for imbalanced datasets?

Because a model can achieve high accuracy by predicting only the majority class.

---

## What is a Confusion Matrix?

A table that summarizes correct and incorrect predictions.

---

## What is Type 1 Error?

False Positive.

---

## What is Type 2 Error?

False Negative.

---

## What is Precision?

Out of all predicted positives, how many were actually positive.

---

## What is Recall?

Out of all actual positives, how many were correctly identified.

---

## When is Recall more important than Precision?

Disease Detection and Fraud Detection.

---

## When is Precision more important than Recall?

Spam Detection and Recommendation Systems.

---

## What is F1 Score?

A metric that balances Precision and Recall.

---

## What does ROC-AUC measure?

The model's ability to distinguish between classes across all thresholds.

---

# Revision Notes

```text
Accuracy
↓
Correct Predictions

Confusion Matrix
↓
TP TN FP FN

FP
↓
Type 1 Error

FN
↓
Type 2 Error

Precision
↓
TP / (TP + FP)

Recall
↓
TP / (TP + FN)

F1 Score
↓
Balance of Precision and Recall

ROC Curve
↓
TPR vs FPR

ROC-AUC
↓
Area Under ROC Curve

AUC = 1
↓
Perfect Model

AUC = 0.5
↓
Random Guessing
```

---

# Conclusion

Classification Metrics help evaluate classification models beyond simple accuracy. Metrics such as Precision, Recall, F1 Score, and ROC-AUC provide deeper insights into model performance, especially when dealing with imbalanced datasets. Understanding these metrics is essential for selecting, evaluating, and improving classification models in real-world machine learning applications.

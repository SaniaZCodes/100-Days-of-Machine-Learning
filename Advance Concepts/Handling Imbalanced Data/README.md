# ⚖️ Imbalanced Data Handling

## 📌 Overview

In many real-world Machine Learning problems, the target classes are not equally distributed.

For example:

- Credit Card Fraud Detection
- Disease Prediction
- Loan Default Prediction
- Customer Churn Prediction

In such datasets, one class significantly outnumbers the other, creating an imbalanced dataset.

Imbalanced data can lead to misleading model performance and poor minority-class prediction.

---

# 🎯 What is Imbalanced Data?

An imbalanced dataset is a dataset where one class contains significantly more observations than another class.

### Example

| Class | Count |
|---------|---------|
| Non-Diabetic | 950 |
| Diabetic | 50 |

Here:

```text
950 ≠ 50
```

The dataset is imbalanced.

---

# 🚨 Why is Imbalanced Data a Problem?

Suppose:

```text
Healthy Patients = 950

Diabetic Patients = 50
```

A model predicts:

```text
Everyone = Healthy
```

Result:

```text
950 Correct

50 Incorrect
```

Accuracy:

```text
950 / 1000

= 95%
```

Looks excellent ✅

But:

```text
50 diabetic patients missed
```

Model is actually poor ❌

---

# 📊 Why Accuracy Becomes Misleading?

In imbalanced datasets, Accuracy alone cannot be trusted.

Instead, more important metrics are:

- Precision
- Recall
- F1 Score
- ROC-AUC

These metrics provide a more realistic evaluation of model performance.

---

# 🛠️ Techniques to Handle Imbalanced Data

Three major approaches are commonly used:

```text
1. Undersampling

2. Oversampling

3. SMOTE
```

---

# 1️⃣ Undersampling

Undersampling balances the dataset by reducing observations from the majority class.

### Example

Before:

```text
Class 0 = 950

Class 1 = 50
```

After:

```text
Class 0 = 50

Class 1 = 50
```

Majority observations are removed.

---

## Advantages

✅ Balanced classes

✅ Faster training

✅ Simple implementation

---

## Disadvantages

❌ Information loss

❌ Potential loss of important patterns

❌ Reduced training data

---

## Easy Memory Trick

```text
Undersampling

=

Delete Data ✂️
```

---

# 2️⃣ Oversampling

Oversampling balances the dataset by duplicating observations from the minority class.

### Example

Before:

```text
Class 0 = 950

Class 1 = 50
```

After:

```text
Class 0 = 950

Class 1 = 950
```

Minority samples are repeatedly copied.

---

## Advantages

✅ No loss of majority-class data

✅ Simple implementation

---

## Disadvantages

❌ Overfitting risk

❌ Duplicate observations

❌ Model may memorize repeated samples

---

## Easy Memory Trick

```text
Oversampling

=

Copy Data 📄
```

---

# 3️⃣ SMOTE (Most Important)

SMOTE stands for:

```text
Synthetic Minority Oversampling Technique
```

Instead of duplicating existing samples, SMOTE generates completely new synthetic observations.

---

# 🧠 How SMOTE Works

Suppose minority-class observations are:

```text
Sample A

Sample B
```

Simple Oversampling:

```text
A

A

A

B

B
```

Just copies data.

---

SMOTE generates:

```text
A

New Synthetic Sample

B
```

New observations are created between similar minority samples.

---

# 🌟 Visual Intuition

Before SMOTE:

```text
A ---------------- B
```

After SMOTE:

```text
A ------- N ------- B
```

Where:

```text
N = New Synthetic Sample
```

---

# Why SMOTE Is Better

### Oversampling

```text
Copy Existing Data
```

---

### SMOTE

```text
Generate New Data
```

Result:

✅ Better generalization

✅ Reduced overfitting

✅ Improved minority-class learning

---

# ⚔️ Undersampling vs Oversampling vs SMOTE

| Technique | Idea |
|------------|--------|
| Undersampling | Remove majority samples |
| Oversampling | Duplicate minority samples |
| SMOTE | Generate synthetic minority samples |

---

# 🩺 Example in Healthcare

Suppose:

```text
Healthy Patients = 500

Diabetic Patients = 100
```

SMOTE can generate synthetic diabetic observations and create:

```text
Healthy = 500

Diabetic = 500
```

Balanced dataset.

---

# 📅 When Should SMOTE Be Applied?

This is very important.

✅ Correct Workflow:

```text
EDA
      ↓

Train-Test Split
      ↓

Preprocessing
      ↓

Scaling
      ↓

SMOTE
      ↓

Model Training
```

---

❌ Wrong Workflow:

```text
SMOTE
      ↓

Train-Test Split
```

This causes:

```text
Data Leakage
```

---

# ✅ Important Rule

Apply SMOTE only on:

```python
X_train

y_train
```

Never apply SMOTE on:

```python
X_test

y_test
```

---

# 📊 Applications

- Credit Card Fraud Detection
- Disease Prediction
- Loan Default Prediction
- Customer Churn Prediction
- Insurance Claim Prediction

---

# ✅ Advantages of SMOTE

- Reduces class imbalance
- Generates synthetic data
- Prevents minority-class neglect
- Better than simple duplication
- Improves Recall in many cases

---

# ❌ Disadvantages of SMOTE

- Synthetic data may introduce noise
- Can increase training time
- May generate unrealistic observations if data quality is poor

---

# 🎓 Interview Questions

### What is Imbalanced Data?

An imbalanced dataset is one where one class contains significantly more observations than another class.

---

### Why is Accuracy unreliable in Imbalanced Data?

Because a model may achieve high accuracy by always predicting the majority class while completely ignoring the minority class.

---

### What is Undersampling?

Undersampling balances classes by removing observations from the majority class.

---

### What is Oversampling?

Oversampling balances classes by duplicating observations from the minority class.

---

### What is SMOTE?

SMOTE (Synthetic Minority Oversampling Technique) generates new synthetic minority-class observations rather than duplicating existing samples.

---

### Which is generally better: Oversampling or SMOTE?

SMOTE is generally preferred because it creates synthetic observations instead of simply copying existing ones.

---

### When should SMOTE be applied?

After Train-Test Split and only on the training dataset.

---

# 💻 Implementation Code

## Checking Class Distribution

```python
print(y_train.value_counts())
```

---

## Random Oversampling

```python
from imblearn.over_sampling import RandomOverSampler

ros = RandomOverSampler(
    random_state=42
)

X_train_over, y_train_over = ros.fit_resample(
    X_train,
    y_train
)

print(y_train_over.value_counts())
```

---

## Random Undersampling

```python
from imblearn.under_sampling import RandomUnderSampler

rus = RandomUnderSampler(
    random_state=42
)

X_train_under, y_train_under = rus.fit_resample(
    X_train,
    y_train
)

print(y_train_under.value_counts())
```

---

## SMOTE

```python
from imblearn.over_sampling import SMOTE

smote = SMOTE(
    random_state=42
)

X_train_smote, y_train_smote = smote.fit_resample(
    X_train,
    y_train
)

print(y_train_smote.value_counts())
```

---

## Train Model After SMOTE

```python
from sklearn.ensemble import RandomForestClassifier

rf = RandomForestClassifier(
    random_state=42
)

rf.fit(
    X_train_smote,
    y_train_smote
)

y_pred = rf.predict(X_test)
```

---

# 📌 Key Takeaways

✅ Imbalanced Data occurs when one class has significantly more observations than another.

✅ Accuracy alone is unreliable.

✅ Important Metrics:
- Precision
- Recall
- F1 Score
- ROC-AUC

✅ Undersampling removes majority-class samples.

✅ Oversampling duplicates minority-class samples.

✅ SMOTE generates synthetic minority-class observations.

✅ SMOTE is generally preferred over simple oversampling.

✅ Apply SMOTE after Train-Test Split and only on training data.

---

# 🏁 Conclusion

Imbalanced datasets are common in real-world Machine Learning problems and can significantly affect model performance. Traditional accuracy metrics often become misleading, making Recall, Precision, F1 Score, and ROC-AUC more useful evaluation measures.

Techniques such as Undersampling, Oversampling, and SMOTE help balance class distributions. Among them, SMOTE is widely used because it creates synthetic minority-class observations instead of simply duplicating existing data, leading to better generalization and improved predictive performance.

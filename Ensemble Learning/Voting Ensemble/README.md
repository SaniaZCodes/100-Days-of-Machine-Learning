# 📊 Voting Ensemble

## 📌 Overview

Voting Ensemble is the simplest ensemble learning technique in Machine Learning.

Instead of relying on a single model, multiple machine learning models are trained independently and their predictions are combined to produce a final prediction.

The core idea is:

> A group of models often performs better than a single model.

---

# 🎯 Why Voting Ensemble?

Individual models have strengths and weaknesses.

For example:

- Logistic Regression may perform well on linear relationships.
- KNN may capture local patterns.
- SVM may find better decision boundaries.

By combining their predictions, overall performance can often be improved.

---

# 🧠 Core Idea

Multiple models make predictions independently.

```text
Model 1
Model 2
Model 3
     ↓
Combine Predictions
     ↓
Final Prediction
```

Example:

```text
Logistic Regression
KNN
SVM
      ↓
Voting Ensemble
      ↓
Final Prediction
```

---

# 🗳️ Voting Classifier

Voting Classifier is used for Classification Problems.

Examples:

- Disease Prediction
- Spam Detection
- Customer Churn Prediction

Two types of Voting Classifier exist:

- Hard Voting
- Soft Voting

---

# 🗳️ Hard Voting

Hard Voting uses the final predictions of each model.

### Example

| Model | Prediction |
|---------|---------|
| Logistic Regression | Diabetes (1) |
| KNN | No Diabetes (0) |
| SVM | Diabetes (1) |

Final Decision:

```text
1 receives 2 votes
0 receives 1 vote
```

Final Prediction:

```text
Diabetes (1)
```

### Working

```text
Model Predictions
       ↓
Majority Vote
       ↓
Final Prediction
```

---

# 🎯 Soft Voting

Soft Voting uses prediction probabilities instead of final predictions.

### Example

| Model | Probability of Diabetes |
|---------|---------|
| Logistic Regression | 0.80 |
| KNN | 0.60 |
| SVM | 0.90 |

Average Probability:

```text
(0.80 + 0.60 + 0.90) / 3

= 0.766
```

Final Prediction:

```text
76.6% probability of Diabetes
```

### Working

```text
Model Probabilities
       ↓
Average Probability
       ↓
Final Prediction
```

---

# ⚔️ Hard Voting vs Soft Voting

| Hard Voting | Soft Voting |
|------------|-------------|
| Uses final predictions | Uses probabilities |
| Majority vote decides | Average probability decides |
| Simpler approach | More informative approach |
| Ignores confidence level | Considers confidence level |
| Usually less effective | Often performs better |

---

# 📈 Voting Regressor

Voting Regressor is used for Regression Problems.

Examples:

- House Price Prediction
- Salary Prediction
- Sales Forecasting

Instead of voting, predictions are averaged.

### Example

| Model | House Price Prediction |
|---------|---------|
| Linear Regression | 50 Lakh |
| Decision Tree | 55 Lakh |
| KNN Regressor | 60 Lakh |

Final Prediction:

```text
(50 + 55 + 60) / 3

= 55 Lakh
```

### Working

```text
Model Predictions
       ↓
Average
       ↓
Final Prediction
```

---

# 🔄 Voting Classifier vs Voting Regressor

| Voting Classifier | Voting Regressor |
|------------------|------------------|
| Used for Classification | Used for Regression |
| Produces Class Labels | Produces Numeric Values |
| Uses Hard Voting or Soft Voting | Uses Averaging |
| Example: Diabetes Prediction | Example: House Price Prediction |

---

# ✅ Advantages of Voting Ensemble

- Easy to implement
- Improves model stability
- Reduces individual model errors
- Better generalization
- Often achieves higher performance than a single model

---

# ❌ Disadvantages of Voting Ensemble

- Computationally more expensive than a single model
- Requires multiple trained models
- Harder to interpret
- Performance depends on the quality of individual models

---

# 🎓 Interview Questions

### What is Voting Ensemble?

Voting Ensemble is an ensemble learning technique that combines predictions from multiple machine learning models to generate a final prediction.

### What is Hard Voting?

Hard Voting combines the predicted class labels of multiple classifiers and selects the class that receives the majority vote.

### What is Soft Voting?

Soft Voting combines the predicted probabilities of multiple classifiers and selects the class with the highest average probability.

### Which is usually better: Hard Voting or Soft Voting?

Soft Voting is generally preferred because it considers the confidence of each model's prediction.

### What is Voting Regressor?

Voting Regressor combines predictions from multiple regression models and calculates their average to produce the final prediction.

---

# 💻 Implementation Code

## Voting Classifier (Hard Voting)

```python
from sklearn.ensemble import VotingClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.neighbors import KNeighborsClassifier
from sklearn.svm import SVC

lr = LogisticRegression()
knn = KNeighborsClassifier()
svm = SVC()

voting_clf = VotingClassifier(
    estimators=[
        ('lr', lr),
        ('knn', knn),
        ('svm', svm)
    ],
    voting='hard'
)

voting_clf.fit(X_train, y_train)

y_pred = voting_clf.predict(X_test)
```

---

## Voting Classifier (Soft Voting)

```python
from sklearn.ensemble import VotingClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.neighbors import KNeighborsClassifier
from sklearn.svm import SVC

lr = LogisticRegression()
knn = KNeighborsClassifier()
svm = SVC(probability=True)

voting_clf = VotingClassifier(
    estimators=[
        ('lr', lr),
        ('knn', knn),
        ('svm', svm)
    ],
    voting='soft'
)

voting_clf.fit(X_train, y_train)

y_pred = voting_clf.predict(X_test)
```

---

## Voting Regressor

```python
from sklearn.ensemble import VotingRegressor
from sklearn.linear_model import LinearRegression
from sklearn.tree import DecisionTreeRegressor
from sklearn.neighbors import KNeighborsRegressor

lr = LinearRegression()
dt = DecisionTreeRegressor()
knn = KNeighborsRegressor()

voting_reg = VotingRegressor(
    estimators=[
        ('lr', lr),
        ('dt', dt),
        ('knn', knn)
    ]
)

voting_reg.fit(X_train, y_train)

y_pred = voting_reg.predict(X_test)
```

---

# 📌 Key Takeaways

✅ Voting Ensemble combines multiple models to improve performance.

✅ Voting Classifier is used for classification tasks.

✅ Hard Voting uses class labels.

✅ Soft Voting uses probabilities.

✅ Soft Voting is generally preferred because it considers model confidence.

✅ Voting Regressor is used for regression tasks.

✅ Voting Regressor combines predictions by averaging.

✅ Multiple models often perform better than a single model.

---

# 🏁 Conclusion

Voting Ensemble is the simplest ensemble learning technique and serves as the foundation of ensemble methods.

For classification tasks, it uses Hard Voting or Soft Voting to combine predictions from multiple classifiers.

For regression tasks, it averages predictions using a Voting Regressor.

Among the two classification approaches, Soft Voting is generally preferred because it considers the confidence level of each model and often produces better results.

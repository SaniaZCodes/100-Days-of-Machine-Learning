# 🚀 Gradient Boosting

## 📌 Overview

Gradient Boosting is a powerful Boosting algorithm that builds models sequentially.

Unlike AdaBoost, which focuses on misclassified observations, Gradient Boosting focuses on the errors (residuals) made by previous models.

Each new model attempts to correct the mistakes of the previous model, gradually improving overall performance.

Gradient Boosting serves as the foundation for advanced algorithms such as XGBoost, LightGBM, and CatBoost.

---

# 🎯 Why Gradient Boosting?

Traditional machine learning models often leave prediction errors behind.

Instead of training one large model, Gradient Boosting builds several small models that continuously correct previous errors.

### Core Idea

```text
Model 1
    ↓

Calculate Errors
    ↓

Model 2 Learns Errors
    ↓

Calculate Remaining Errors
    ↓

Model 3 Learns Remaining Errors
    ↓

Final Strong Model
```

---

# 🧠 What is Gradient Boosting?

Gradient Boosting is a boosting technique that creates models sequentially.

Each new model learns the residual errors made by the previous model.

### Gradient Boosting Formula

```text
Gradient Boosting

=

Weak Learners
+
Residual Learning
+
Sequential Training
```

---

# 🔍 What are Residuals?

Residuals represent the errors made by a model.

### Formula

```text
Residual

=

Actual Value - Predicted Value
```

### Example

```text
Actual Value = 100

Predicted Value = 80

Residual = 20
```

This residual becomes the new target for the next learner.

---

# ⚙️ Working of Gradient Boosting

## Step 1: Initial Prediction

Gradient Boosting starts with a simple prediction.

For regression problems, this is usually:

```text
Mean of Target Variable
```

Example:

```text
Target Values

100
80
60

Mean = 80
```

Initial prediction:

```text
80
80
80
```

---

## Step 2: Calculate Residuals

```text
Actual - Predicted
```

Example:

```text
100 - 80 = 20

80 - 80 = 0

60 - 80 = -20
```

Residuals:

```text
20
0
-20
```

---

## Step 3: Train Tree on Residuals

The next tree is trained using residuals instead of actual target values.

The model tries to learn:

```text
20
0
-20
```

instead of:

```text
100
80
60
```

---

## Step 4: Update Predictions

New predictions are calculated as:

```text
Old Prediction
+
New Tree Prediction
```

Example:

```text
80 + 15 = 95
```

Prediction becomes closer to the actual value.

---

## Step 5: Calculate New Residuals

Again:

```text
Residual
=
Actual - New Prediction
```

Residuals become smaller.

---

## Step 6: Repeat

The process continues:

```text
Compute Residuals
      ↓

Train New Tree
      ↓

Update Predictions
      ↓

Compute New Residuals
```

until the desired number of estimators is reached.

---

# 🌳 Gradient Boosting for Regression

Regression uses numeric targets.

Examples:

- House Price Prediction
- Salary Prediction
- Sales Forecasting
- Temperature Prediction

### Workflow

```text
Mean Prediction
      ↓

Residuals
      ↓

Tree Learns Residuals
      ↓

Updated Prediction
      ↓

Smaller Residuals
      ↓

Repeat
```

---

# 🎯 Gradient Boosting for Classification

Classification problems contain class labels.

Examples:

- Diabetes Prediction
- Heart Disease Prediction
- Spam Detection

Instead of directly learning the labels, Gradient Boosting continuously improves prediction probabilities and decision boundaries by correcting errors step-by-step.

### Workflow

```text
Initial Classification Prediction
             ↓

Prediction Errors
             ↓

Tree Learns Errors
             ↓

Updated Prediction
             ↓

Smaller Errors
             ↓

Repeat
```

---

# ⚔️ AdaBoost vs Gradient Boosting

| AdaBoost | Gradient Boosting |
|-----------|------------------|
| Focuses on wrong samples | Focuses on residual errors |
| Uses sample weights | Uses residual learning |
| Decision Stumps are common | Small Decision Trees are common |
| Sequential Training | Sequential Training |
| Reduces Bias | Reduces Bias |
| Simpler Algorithm | More Powerful Algorithm |

---

# 🌲 Why Gradient Boosting Works?

Every new tree focuses on the remaining mistakes.

Instead of repeatedly predicting the target variable, trees focus only on what is still not correct.

This allows the model to gradually improve its predictions.

---

# 🎛️ Important Hyperparameters

## n_estimators

Number of trees.

Example:

```python
n_estimators=100
```

Means:

```text
100 Trees
```

---

## learning_rate

Controls how much each tree contributes.

### Smaller Value

```text
Slower Learning

Better Generalization
```

---

### Larger Value

```text
Faster Learning

Higher Risk of Overfitting
```

---

## max_depth

Maximum depth of individual trees.

Controls model complexity.

---

## min_samples_split

Minimum samples required before splitting a node.

---

## min_samples_leaf

Minimum observations allowed in a leaf node.

---

# ⚖️ Bias-Variance Characteristics

### Decision Tree

```text
Low Bias
High Variance
```

---

### Gradient Boosting

```text
Low Bias
Controlled Variance
```

Through sequential corrections, Gradient Boosting produces highly accurate models.

---

# ✅ Advantages of Gradient Boosting

- High predictive performance
- Handles complex relationships
- Works well on structured data
- Reduces bias effectively
- Foundation of many winning machine learning solutions
- Supports both regression and classification

---

# ❌ Disadvantages of Gradient Boosting

- Slower training due to sequential learning
- More sensitive to hyperparameters
- Can overfit if not tuned properly
- More computationally expensive than Bagging

---

# 🎓 Interview Questions

### What is Gradient Boosting?

Gradient Boosting is an ensemble learning technique where each new model learns the residual errors made by previous models.

---

### What are residuals?

Residuals represent prediction errors.

```text
Residual
=
Actual - Predicted
```

---

### Why is it called Gradient Boosting?

Because it moves predictions in the direction that reduces the error (gradient) at every iteration.

---

### Difference Between AdaBoost and Gradient Boosting?

AdaBoost focuses on misclassified observations using sample weights, while Gradient Boosting focuses on prediction errors (residuals).

---

### What is the role of learning_rate?

It controls the contribution of each tree to the final prediction.

---

### What is the role of n_estimators?

It determines how many trees will be built sequentially.

---

# 💻 Implementation Code

## Gradient Boosting Regressor

```python
from sklearn.ensemble import GradientBoostingRegressor

gbr = GradientBoostingRegressor(
    n_estimators=100,
    learning_rate=0.1,
    max_depth=3,
    random_state=42
)

gbr.fit(X_train, y_train)

y_pred = gbr.predict(X_test)
```

---

## Gradient Boosting Classifier

```python
from sklearn.ensemble import GradientBoostingClassifier

gbc = GradientBoostingClassifier(
    n_estimators=100,
    learning_rate=0.1,
    max_depth=3,
    random_state=42
)

gbc.fit(X_train, y_train)

y_pred = gbc.predict(X_test)
```

---

## Hyperparameter Tuning Using GridSearchCV

```python
from sklearn.ensemble import GradientBoostingClassifier
from sklearn.model_selection import GridSearchCV

params = {
    'n_estimators':[50,100,200],
    'learning_rate':[0.01,0.1,0.5],
    'max_depth':[2,3,4]
}

grid = GridSearchCV(
    GradientBoostingClassifier(random_state=42),
    param_grid=params,
    cv=5,
    scoring='accuracy'
)

grid.fit(X_train, y_train)

print(grid.best_params_)
print(grid.best_score_)
```

---

## Hyperparameter Tuning Using RandomizedSearchCV

```python
from sklearn.ensemble import GradientBoostingClassifier
from sklearn.model_selection import RandomizedSearchCV

params = {
    'n_estimators':[50,100,200,300],
    'learning_rate':[0.01,0.1,0.5,1],
    'max_depth':[2,3,4,5]
}

random_search = RandomizedSearchCV(
    GradientBoostingClassifier(random_state=42),
    param_distributions=params,
    n_iter=10,
    cv=5,
    scoring='accuracy',
    random_state=42
)

random_search.fit(X_train, y_train)

print(random_search.best_params_)
print(random_search.best_score_)
```

---

# 📌 Key Takeaways

✅ Gradient Boosting is a Boosting algorithm.

✅ Models are trained sequentially.

✅ Each tree learns residual errors.

✅ Residual = Actual − Predicted.

✅ New trees continuously correct previous mistakes.

✅ More powerful than AdaBoost in many situations.

✅ Important hyperparameters:
- n_estimators
- learning_rate
- max_depth

✅ Works for both Classification and Regression.

✅ Forms the foundation of XGBoost, LightGBM, and CatBoost.

---

# 🏁 Conclusion

Gradient Boosting is one of the most influential ensemble learning algorithms in Machine Learning. It improves predictions by sequentially training weak learners that focus on correcting previous errors.

By learning residuals and making gradual improvements, Gradient Boosting achieves strong predictive performance and serves as the foundation for advanced boosting techniques such as XGBoost.

Its ability to handle both regression and classification tasks makes it one of the most powerful algorithms for structured data problems.

# Regression Evaluation Metrics

## Overview

After building a regression model, the next step is to evaluate how well the model performs.

Regression metrics help us measure the difference between actual values and predicted values.

Common regression metrics include:

- MAE (Mean Absolute Error)
- MSE (Mean Squared Error)
- RMSE (Root Mean Squared Error)
- R² Score
- Adjusted R² Score

---

# Why Do We Need Regression Metrics?

Suppose a house price prediction model predicts:

| Actual Price | Predicted Price |
|-------------|----------------|
| 100 | 90 |
| 200 | 220 |
| 300 | 250 |

The question is:

> How good are these predictions?

Regression metrics answer this question.

---

# Mean Absolute Error (MAE)

## What is MAE?

MAE calculates the average absolute difference between actual values and predicted values.

## Formula

```text
MAE = Σ|Actual - Predicted| / n
```

## Intuition

MAE tells us:

> On average, how much the model is making a mistake.

## Example

Actual Values:

```text
100, 200, 300
```

Predicted Values:

```text
90, 220, 250
```

Errors:

```text
10, 20, 50
```

MAE:

```text
(10 + 20 + 50) / 3

= 26.67
```

## Interpretation

```text
MAE = 26.67
```

means:

> The model is making an average error of 26.67 units.

---

## Advantages of MAE

- Easy to understand
- Easy to interpret
- Less sensitive to outliers

---

## Disadvantages of MAE

- Does not heavily penalize large errors
- All mistakes are treated equally

---

# Mean Squared Error (MSE)

## What is MSE?

MSE calculates the average of squared prediction errors.

## Formula

```text
MSE = Σ(Actual - Predicted)² / n
```

## Intuition

MSE gives larger penalties to larger mistakes.

## Example

Errors:

```text
10, 20, 50
```

Squared Errors:

```text
100, 400, 2500
```

MSE:

```text
(100 + 400 + 2500) / 3

= 1000
```

---

## Advantages of MSE

- Penalizes large mistakes heavily
- Useful during model training
- Widely used in machine learning algorithms

---

## Disadvantages of MSE

- Difficult to interpret
- Units become squared

Example:

```text
House Price → Rupees

MSE → Rupees²
```

---

# Root Mean Squared Error (RMSE)

## What is RMSE?

RMSE is simply the square root of MSE.

## Formula

```text
RMSE = √MSE
```

## Intuition

RMSE converts MSE back into the original units.

## Example

```text
MSE = 100
```

RMSE:

```text
√100 = 10
```

---

## Advantages of RMSE

- Easy to interpret
- Same unit as target variable
- Penalizes large errors more than MAE

---

## Disadvantages of RMSE

- Sensitive to outliers
- Large errors significantly affect the score

---

# MAE vs RMSE

| MAE | RMSE |
|------|------|
| Average absolute error | Square root of squared error |
| Easy to understand | Gives more importance to large errors |
| Less sensitive to outliers | More sensitive to outliers |
| All errors treated equally | Large errors heavily penalized |

---

# R² Score

## What is R² Score?

It tells ka model na kitna acha predict kiya hy?
R² Score measures how much variation in the target variable is explained by the model.

## Range

```text
0 → 1
```

---

## Interpretation

### R² = 0

```text
Model learned nothing
```

---

### R² = 0.50

```text
Model explains 50% of the variation
```

---

### R² = 0.80

```text
Model explains 80% of the variation
```

---

### R² = 1

```text
Perfect model
```

---

## Intuition

R² tells us:

> How well the model understands the relationship in the data.

---

## Advantages of R²

- Easy comparison between models
- Widely used
- Provides overall model quality

---

## Disadvantages of R²

- Can increase even when irrelevant features are added
- Not always reliable for multiple regression

---

# Adjusted R² Score

## What is Adjusted R²?

Adjusted R² is an improved version of R².

It penalizes the addition of unnecessary features.

---

## Why Do We Need It?

Suppose:

```text
Feature 1 = Area
```

R²:

```text
0.80
```

Now add an irrelevant feature:

```text
Favorite Color
```

Normal R² may increase slightly.

This can be misleading.

Adjusted R² solves this problem.

---

## Intuition

Adjusted R² asks:

> Did the new feature genuinely improve the model?

If YES:

```text
Adjusted R² Increases
```

If NO:

```text
Adjusted R² Decreases
```

---

## Advantages of Adjusted R²

- More reliable than R²
- Penalizes unnecessary features
- Useful in Multiple Linear Regression

---

## Disadvantages of Adjusted R²

- Slightly harder to understand
- Mostly useful when multiple features exist

---

# When to Use Each Metric?

## Use MAE When:

- Easy interpretation is needed
- Outliers are not very important

---

## Use RMSE When:

- Large mistakes should be punished
- Outliers are important

---

## Use R² When:

- Comparing regression models
- Measuring explained variance

---

## Use Adjusted R² When:

- Working with Multiple Linear Regression
- Comparing models with different numbers of features

---

# sklearn Implementation

```python
from sklearn.metrics import (
    mean_absolute_error,
    mean_squared_error,
    r2_score
)

mae = mean_absolute_error(y_test, y_pred)

mse = mean_squared_error(y_test, y_pred)

rmse = mean_squared_error(
    y_test,
    y_pred,
    squared=False
)

r2 = r2_score(y_test, y_pred)
```

---

# Interview Questions

## Q1. What is MAE?

MAE is the average absolute difference between actual and predicted values.

---

## Q2. What is MSE?

MSE is the average squared difference between actual and predicted values.

---

## Q3. What is RMSE?

RMSE is the square root of MSE and is expressed in the original unit of the target variable.

---

## Q4. Why do we square errors in MSE?

To penalize larger mistakes and prevent positive and negative errors from cancelling each other.

---

## Q5. Which metric is more sensitive to outliers?

RMSE and MSE.

---

## Q6. What does R² Score measure?

R² measures how much variation in the target variable is explained by the model.

---

## Q7. What is the range of R²?

```text
0 to 1
```

---

## Q8. What is a perfect R² Score?

```text
R² = 1
```

---

## Q9. Why do we use Adjusted R²?

Adjusted R² penalizes unnecessary features and provides a more reliable evaluation.

---

## Q10. Difference between R² and Adjusted R²?

R² may increase when extra features are added.

Adjusted R² increases only when those features actually improve the model.

---

# Revision Notes

```text
MAE
↓
Average Absolute Error

MSE
↓
Average Squared Error

RMSE
↓
Square Root of MSE

R²
↓
How much variance is explained

Adjusted R²
↓
R² with penalty for unnecessary features

Most Sensitive To Outliers?
↓
MSE and RMSE

Most Easily Interpretable?
↓
MAE

Best For Multiple Regression?
↓
Adjusted R²
```

---

# Summary

Regression metrics are used to evaluate the performance of regression models.

- MAE measures average error
- MSE measures squared error
- RMSE measures error in original units
- R² measures explained variance
- Adjusted R² penalizes unnecessary features

Choosing the right metric depends on the problem and business requirements.

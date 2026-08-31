# Assumptions of Linear Regression

## Overview

Linear Regression works best when certain assumptions are satisfied.

These assumptions help ensure that the model is reliable, interpretable, and produces meaningful results.

If these assumptions are heavily violated, the model may still make predictions, but the results and interpretations become less trustworthy.

---

# Why Do We Need Assumptions?

Linear Regression tries to find the best relationship between input features and the target variable.

For accurate predictions and meaningful coefficients, some conditions should hold true in the dataset.

These conditions are known as the assumptions of Linear Regression.

---

# Top 5 Assumptions of Linear Regression

1. Linearity
2. No Multicollinearity
3. Homoscedasticity
4. Normality of Residuals
5. Independence of Errors

---

# 1. Linearity

## What is Linearity?

Linearity means there should be an approximately linear relationship between the independent variables and the target variable.

In simple words:

> When the feature changes, the target should change in a roughly straight-line pattern.

---

## Good Example

```text
Experience ↑
Salary ↑
```

The relationship follows a roughly straight trend.

---

## Bad Example

```text
Feature ↑
Target follows a curve
```

A highly curved relationship may not be suitable for Linear Regression.

---

## Why Is It Important?

Linear Regression is designed to fit a straight-line relationship.

If the actual relationship is highly nonlinear, prediction performance may decrease.

---

## Interview Answer

Linearity means there should be an approximately linear relationship between the features and the target variable.

---

# 2. No Multicollinearity

## What is Multicollinearity?

Multicollinearity occurs when two or more independent variables are highly correlated with each other.

In simple words:

> Features should not contain almost the same information.

---

## Example

```text
Area in Square Feet

Area in Square Meters
```

Both represent the same information.

---

Another Example:

```text
Age

Year Built
```

These features are often highly related.

---

## Why Is It a Problem?

The model becomes confused about which feature is actually contributing to the prediction.

This can make coefficients unstable and difficult to interpret.

---

## Easy Memory

```text
Features should not copy each other.
```

---

## Interview Answer

Multicollinearity occurs when independent variables are highly correlated with each other.

---

# 3. Homoscedasticity

## What is Homoscedasticity?

Homoscedasticity means that the variance of residuals remains approximately constant.

In simple words:

> Prediction errors should have a similar spread across all prediction levels.

---

## Good Example

```text
Small Houses → Small Errors

Medium Houses → Small Errors

Large Houses → Small Errors
```

Error spread remains balanced.

---

## Bad Example

```text
Small Houses → Small Errors

Large Houses → Huge Errors
```

Error spread changes significantly.

---

## Why Is It Important?

Unequal error spread can reduce the reliability of coefficient estimates.

---

## Easy Memory

```text
Error variance should remain constant.
```

---

## Interview Answer

Homoscedasticity means the residuals should have approximately constant variance across all levels of prediction.

---

# 4. Normality of Residuals

## What are Residuals?

Residuals are the differences between actual and predicted values.

Formula:

```text
Residual = Actual - Predicted
```

---

## What is Normality of Residuals?

Residuals should follow an approximately normal distribution.

---

## Good Example

```text
-5
-3
-1
 0
 1
 3
 5
```

Balanced around zero.

---

## Bad Example

```text
100
120
150
```

Highly skewed errors.

---

## Why Is It Important?

Normal residuals help ensure reliable statistical interpretation and confidence intervals.

---

## Easy Memory

```text
Residuals should look normally distributed.
```

---

## Interview Answer

The residuals should be approximately normally distributed around zero.

---

# 5. Independence of Errors

## What is Independence of Errors?

Errors should not depend on previous errors.

In simple words:

> One prediction error should not influence another prediction error.

---

## Good Example

Independent observations collected from different houses.

---

## Bad Example

Time-series data where today's error affects tomorrow's error.

---

## Why Is It Important?

Dependent errors may indicate that the model is missing important patterns in the data.

---

## Easy Memory

```text
One error should not influence another error.
```

---

## Interview Answer

Independence of errors means residuals should not be correlated with each other.

---

# Residuals Explained

Residuals are the differences between actual and predicted values.

Formula:

```text
Residual = Actual - Predicted
```

Example:

```text
Actual Price = 300000

Predicted Price = 280000
```

Residual:

```text
20000
```

---

# Most Important Assumptions in Practice

In real-world projects, these assumptions are often given the most attention:

✅ Linearity

✅ No Multicollinearity

These are commonly checked before trusting Linear Regression results.

---

# Advantages of Following Assumptions

- Better model reliability
- Better interpretability
- More stable coefficients
- More meaningful predictions
- Improved statistical validity

---

# What Happens If Assumptions Are Violated?

The model may still make predictions, but:

- Coefficients may become unreliable.
- Performance may decrease.
- Interpretation becomes difficult.
- Confidence in conclusions reduces.

---

# Common Detection Techniques

## Linearity

- Scatter Plot
- Residual Plot

---

## Multicollinearity

- Correlation Matrix
- VIF (Variance Inflation Factor)

---

## Homoscedasticity

- Residual Plot

---

## Normality of Residuals

- Histogram
- Q-Q Plot

---

## Independence of Errors

- Durbin-Watson Test

---

# Real World Example

## House Price Prediction

Features:

```text
Area
Bedrooms
Bathrooms
Garage
```

Before using Linear Regression, check:

- Is the relationship approximately linear?
- Are features highly correlated?
- Are residuals normally distributed?
- Is the error variance constant?
- Are observations independent?

---

# Interview Questions

## Q1. What are the assumptions of Linear Regression?

- Linearity
- No Multicollinearity
- Homoscedasticity
- Normality of Residuals
- Independence of Errors

---

## Q2. What is Multicollinearity?

Multicollinearity occurs when independent variables are highly correlated with each other.

---

## Q3. Why is Multicollinearity a problem?

Because it becomes difficult to determine the actual contribution of highly correlated features.

---

## Q4. What are Residuals?

Residuals are the differences between actual and predicted values.

```text
Residual = Actual - Predicted
```

---

## Q5. What is Homoscedasticity?

Homoscedasticity means residuals should have approximately constant variance.

---

## Q6. What is Linearity?

Linearity means there should be an approximately straight-line relationship between features and the target.

---

## Q7. What is Normality of Residuals?

Residuals should be approximately normally distributed around zero.

---

## Q8. What is Independence of Errors?

Errors should not influence each other and should remain independent.

---

## Q9. Which assumptions are most commonly checked in real projects?

- Linearity
- Multicollinearity

---

## Q10. Can Linear Regression work if assumptions are violated?

Yes, but the predictions, coefficients, and interpretations may become less reliable.

---

# Revision Notes

```text
Linearity
↓
Straight-line relationship

Multicollinearity
↓
Features should not be highly correlated

Homoscedasticity
↓
Constant error spread

Normality
↓
Residuals should be normally distributed

Independence
↓
Errors should not depend on each other

Residual
↓
Actual - Predicted
```

---

# Summary

Linear Regression assumes:

1. Linearity
2. No Multicollinearity
3. Homoscedasticity
4. Normality of Residuals
5. Independence of Errors

When these assumptions are reasonably satisfied, Linear Regression becomes more reliable, interpretable, and statistically valid.

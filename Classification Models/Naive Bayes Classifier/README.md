# Naive Bayes Classifier

# Overview

Naive Bayes is a Supervised Machine Learning Classification Algorithm based on Bayes Theorem.

It is widely used for:

- Spam Detection
- Sentiment Analysis
- Text Classification
- Document Categorization
- Medical Diagnosis

Naive Bayes is simple, fast, and performs surprisingly well on many real-world classification problems.

---

# What is Naive Bayes?

Naive Bayes is a Probabilistic Classification Algorithm that predicts the class with the highest probability.

It uses:

```text
Bayes Theorem
+
Feature Independence Assumption
```

to calculate probabilities and make predictions.

---

# Probability Basics

Before understanding Naive Bayes, we need some fundamental probability concepts.

---

# Conditional Probability

Conditional Probability is the probability of an event occurring given that another event has already occurred.

---

## Notation

```text
P(A|B)
```

Read as:

```text
Probability of A given B
```

---

## Example

```text
P(Rain | Cloudy)
```

Meaning:

```text
Probability of Rain
given that it is Cloudy
```

---

## Formula

```text
P(A|B)

=

P(A ∩ B)
---------
P(B)
```

---

# Independent Events

Two events are called Independent if the occurrence of one event does not affect the probability of the other.

---

## Example

```text
Coin Toss

and

Dice Roll
```

The outcome of a coin toss does not affect the outcome of a dice roll.

---

## Property

```text
P(A|B)

=

P(A)
```

---

## Another Property

```text
P(A ∩ B)

=

P(A) × P(B)
```

---

# Mutually Exclusive Events

Two events are Mutually Exclusive if they cannot occur at the same time.

---

## Example

```text
Head

Tail
```

Both cannot occur simultaneously on a single coin toss.

---

## Property

```text
P(A ∩ B)

=

0
```

---

# Bayes Theorem

Bayes Theorem is the foundation of the Naive Bayes Algorithm.

It allows us to calculate:

```text
P(A|B)
```

using information about:

```text
P(B|A)
```

---

## Formula

```text
P(A|B)

=

P(B|A) × P(A)
----------------
P(B)
```

---

# Meaning Of Components

## P(A|B)

Posterior Probability

```text
Probability of A given B
```

---

## P(B|A)

Likelihood

```text
Probability of B given A
```

---

## P(A)

Prior Probability

```text
Initial Probability of A
```

---

## P(B)

Evidence

```text
Probability of Event B
```

---

# Why Bayes Theorem?

Bayes Theorem helps reverse probabilities.

Example:

Known:

```text
P(Positive Test | Disease)
```

Find:

```text
P(Disease | Positive Test)
```

---

# Naive Bayes Intuition

Suppose we have an email:

```text
Win Lottery Prize
```

We want to classify it as:

```text
Spam

or

Not Spam
```

Naive Bayes computes:

```text
P(Spam | Email)

and

P(Not Spam | Email)
```

The class with the higher probability becomes the prediction.

---

# Why Is It Called Naive?

Naive Bayes assumes that all features are independent.

Example:

```text
Win

Lottery

Prize
```

are assumed to be independent features.

---

Reality:

```text
Features are often related.
```

But Naive Bayes ignores this relationship.

This assumption is called the:

```text
Naive Assumption
```

---

# Mathematical Formulation

Bayes Theorem:

```text
P(Class|Features)

=

P(Features|Class) × P(Class)
--------------------------------
P(Features)
```

---

The problem is that:

```text
P(Features|Class)
```

can be difficult to calculate.

---

# Naive Assumption

Because features are assumed independent:

```text
P(F1,F2,F3|Class)
```

becomes:

```text
P(F1|Class)

×

P(F2|Class)

×

P(F3|Class)
```

---

# Final Naive Bayes Formula

```text
P(Class)

×

P(F1|Class)

×

P(F2|Class)

×

P(F3|Class)

...
```

The class with the highest probability is selected.

---

# Important Terms

## Prior Probability

Probability before observing any features.

```text
P(Class)
```

Example:

```text
P(Spam)
```

---

## Likelihood

Probability of observing a feature given a class.

```text
P(Feature|Class)
```

Example:

```text
P(Win|Spam)
```

---

## Posterior Probability

Final probability after considering features.

```text
P(Class|Feature)
```

Example:

```text
P(Spam|Win)
```

---

# Prediction Process

```text
Input Features
↓
Apply Bayes Theorem
↓
Calculate Class Probabilities
↓
Choose Highest Probability
↓
Final Prediction
```

---

# Types of Naive Bayes

There are three commonly used variants.

---

# 1. Gaussian Naive Bayes

Used for:

```text
Numerical Data
```

Examples:

```text
Age

Salary

Marks

Temperature

CGPA
```

Assumption:

```text
Features follow a
Normal (Gaussian) Distribution
```

---

## sklearn Implementation

```python
from sklearn.naive_bayes import GaussianNB

model = GaussianNB()

model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

---

# 2. Multinomial Naive Bayes

Used for:

```text
Count Data
```

Examples:

```text
Word Frequency

Document Classification

Text Classification

Spam Detection
```

---

## sklearn Implementation

```python
from sklearn.naive_bayes import MultinomialNB

model = MultinomialNB()

model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

---

# 3. Bernoulli Naive Bayes

Used for:

```text
Binary Features
```

Examples:

```text
Word Present = 1

Word Absent = 0

Purchased = Yes/No

Clicked = Yes/No
```

---

## sklearn Implementation

```python
from sklearn.naive_bayes import BernoulliNB

model = BernoulliNB()

model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

---

# Complete GaussianNB Example

```python
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import accuracy_score

model = GaussianNB()

model.fit(X_train, y_train)

y_pred = model.predict(X_test)

accuracy = accuracy_score(
    y_test,
    y_pred
)

print("Accuracy:", accuracy)
```

---

# Evaluate Naive Bayes Model

## Accuracy

```python
from sklearn.metrics import accuracy_score

accuracy_score(
    y_test,
    y_pred
)
```

---

## Confusion Matrix

```python
from sklearn.metrics import confusion_matrix

confusion_matrix(
    y_test,
    y_pred
)
```

---

## Classification Report

```python
from sklearn.metrics import classification_report

print(
    classification_report(
        y_test,
        y_pred
    )
)
```

---

# Advantages

✅ Simple and easy to understand

✅ Fast training and prediction

✅ Works well with small datasets

✅ Excellent for text classification

✅ Requires fewer computational resources

✅ Good baseline classifier

---

# Limitations

❌ Assumes features are independent

❌ Assumption is often unrealistic

❌ Can struggle when features are highly correlated

❌ Performance may drop on complex datasets

---

# Real World Applications

## Spam Detection

```text
Spam

Not Spam
```

---

## Sentiment Analysis

```text
Positive Review

Negative Review
```

---

## Document Classification

```text
Sports

Politics

Technology
```

---

## Disease Prediction

```text
Disease

No Disease
```

---

# Interview Questions

## What is Naive Bayes?

Naive Bayes is a probabilistic classification algorithm based on Bayes Theorem.

---

## Why is it called Naive Bayes?

Because it assumes that all features are independent.

---

## What theorem does Naive Bayes use?

```text
Bayes Theorem
```

---

## What is Conditional Probability?

Probability of an event occurring given another event has already occurred.

---

## What are Independent Events?

Events that do not affect each other's probabilities.

---

## What are Mutually Exclusive Events?

Events that cannot occur simultaneously.

---

## What is Prior Probability?

```text
P(Class)
```

Probability before seeing any features.

---

## What is Likelihood?

```text
P(Feature|Class)
```

Probability of a feature given a class.

---

## What is Posterior Probability?

```text
P(Class|Feature)
```

Final probability after considering features.

---

## Which Naive Bayes variant is used for numerical data?

```text
Gaussian Naive Bayes
```

---

## Which Naive Bayes variant is used for text classification?

```text
Multinomial Naive Bayes
```

---

## Which Naive Bayes variant is used for binary features?

```text
Bernoulli Naive Bayes
```

---

# Revision Notes

```text
Conditional Probability
↓
P(A|B)

Independent Events
↓
P(A|B) = P(A)

Mutually Exclusive Events
↓
P(A ∩ B) = 0

Bayes Theorem
↓
P(A|B)

Naive Bayes
↓
Bayes Theorem
+
Feature Independence

Prior
↓
P(Class)

Likelihood
↓
P(Feature|Class)

Posterior
↓
P(Class|Feature)

Prediction
↓
Highest Posterior Probability

GaussianNB
↓
Numerical Data

MultinomialNB
↓
Count Data

BernoulliNB
↓
Binary Data
```

---

# Summary

Naive Bayes is a fast, simple, and powerful probabilistic classification algorithm built upon Bayes Theorem. It assumes feature independence and predicts the class with the highest posterior probability. Depending on the nature of the data, Gaussian, Multinomial, or Bernoulli variants can be used. Despite its simplicity, Naive Bayes remains one of the most effective algorithms for text classification, spam detection, and many real-world machine learning problems.

# Function Transformer

## Purpose

Used to apply custom mathematical transformations on features.

---

## Log Transformation

Use:
- Strong right skew

Code:

FunctionTransformer(np.log1p)

---

## Reciprocal Transformation

Use:
- Very strong skew
- Large values need aggressive shrinking

Code:

FunctionTransformer(lambda x: 1/(x+1))

---

## Square Root Transformation

Use:
- Moderate skew

Code:

FunctionTransformer(np.sqrt)

---

## Golden Line 🌟

Log → Most common

Reciprocal → Strong compression

Square Root → Mild compression

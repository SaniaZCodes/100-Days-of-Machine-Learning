# One Hot Encoding 🔥

## What?

One Hot Encoding converts categorical values into separate binary columns.

---

## Why?

Label Encoding may create a fake order.

Example:

Red → 0

Blue → 1

Green → 2

Machine may think:

Green > Blue > Red

which is incorrect.

---

## Example

Color

Red
Blue
Green

↓

Red Blue Green

1    0    0

0    1    0

0    0    1

---

## Use When

✅ No order exists

Examples:

- Color
- City
- Department
- Country
- Gender

---

## Avoid When

✅ Categories have order

Example:

Small < Medium < Large

Use Ordinal

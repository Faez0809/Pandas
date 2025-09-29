# Pandas — Filling Null Values with `fillna()` 

This part covers how to **fill/replace missing values** in a DataFrame.  
Unlike dropping rows, filling avoids **losing useful data**.

---

## 1) Setup

```python
import pandas as pd

df = pd.read_csv("sample.csv")
```

Data has roll numbers and subject marks (Physics, Chemistry, Math, Computer).

---

## 2) Basic Filling (Scalar Values)

### A) Fill with Zero
```python
df2 = df.fillna(0)
```
- Replaces all `NaN` with 0.  
- Simple, but may distort meaning in some datasets.

### B) Fill with Different Values per Column
```python
df2 = df.fillna({
    "Physics": 90,
    "Math": 30
})
```
- Use a **dictionary**: keys = column names, values = fill numbers.  
- Allows column-specific filling.

---

## 3) Advanced Contextual Filling

### A) Forward Fill (`ffill`)
```python
df2 = df.fillna(method="ffill")
```
- Copies the **previous value** downwards.  
- Example: Row 10 null → filled with Row 9’s value.  
- Limitation: Cannot fill the first row if it’s null.

### B) Backward Fill (`bfill`)
```python
df2 = df.fillna(method="bfill")
```
- Copies the **next value** upwards.  
- Example: Row 10 null → filled with Row 11’s value.

### C) Fill with Statistical Measures (Mean)
```python
avg = df["Physics"].mean()
df2 = df.fillna({"Physics": avg})
```
- Calculate mean/average, then use it to replace nulls.  
- Keeps data distribution more realistic.  
- Works well for numeric columns.

---

## 4) Modifying Original DataFrame

- By default, `fillna()` returns a **new DataFrame**.  
- To update the original directly, use `inplace=True`:

```python
df.fillna(0, inplace=True)
```

- Saves memory, avoids duplicate DataFrame.

---

## 5) Key Takeaways

- `fillna()` is safer than dropping — prevents loss of rows.  
- Scalar fill = simple (0 or fixed values).  
- Dict fill = column-wise control.  
- `ffill` and `bfill` = context-aware filling.  
- Mean (or other stats) = more meaningful replacement.  
- Use `inplace=True` to modify DataFrame directly.

---

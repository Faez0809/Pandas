# Pandas — The `append()` Function 

This part covers the **`append()` function**, which adds one DataFrame below another.

---

## 1) Data Preparation

```python
import pandas as pd

# First DataFrame
df1 = pd.DataFrame({
    "Roll Number": [1, 2, 3, 4, 5],
    "Math": [50, 60, 70, 80, 90],
    "Physics": [65, 75, 85, 95, 55]
})

# Second DataFrame
df2 = pd.DataFrame({
    "Roll Number": [6, 7, 8, 9, 10],
    "Math": [45, 55, 65, 75, 85],
    "Physics": [60, 70, 80, 90, 50]
})
```
- `df1`: roll numbers 1–5.  
- `df2`: roll numbers 6–10.  
- Both have same columns: Roll Number, Math, Physics.

---

## 2) Basic Append

```python
df3 = df1.append(df2)
```
- Adds `df2` rows **after** `df1`.  
- Columns remain the same.  
- Reverse works too: `df2.append(df1)`.

---

## 3) Important Parameters

### A) `ignore_index`
- **Default**: Keeps original indexes.  
  Example: 0–4 (df1) + 0–4 (df2).  
- **With ignore_index=True**: Creates continuous new index.  
  Example: 0–9.

```python
df3 = df1.append(df2, ignore_index=True)
```

### B) `sort`
- Sorts column names alphabetically.  
- Example: Math, Physics, Roll Number.

```python
df3 = df1.append(df2, sort=True)
```

---

## 4) Handling Non-Common Columns

If DataFrames have different columns:  
- Common columns keep values.  
- Missing values become NaN.

Example:  
- `df1` has Chemistry.  
- `df2` does not.  
- After append → Chemistry in `df2` rows = NaN.  
- If `df2` has Math but `df1` doesn’t → Math in `df1` rows = NaN.

---

## 5) Key Takeaways

- `append()` stacks one DataFrame below another.  
- Use `ignore_index=True` to reset index.  
- Use `sort=True` to order columns alphabetically.  
- Different columns → missing ones filled with NaN.  
- Simpler than `merge()` when you just want to **stack rows**.

---

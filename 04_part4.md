# Pandas — Handling Null Values (Missing Data)

This part covers how to **detect and remove null (missing) values** in a DataFrame.  
Null values are important to handle because they can cause errors in analysis and ML models.

---

## 1) Setup and First Checks

```python
import pandas as pd

df = pd.read_csv("sample.csv")
```

- Data has Roll Number, Physics, Chemistry, Math, Computer marks.  
- Check first rows:  
  ```python
  df.head()
  ```

### Detecting Nulls (Boolean)
```python
df.isnull()
```
- Returns `True` if a cell is null, `False` otherwise.  
- Good for inspection, but not for counting.

---

## 2) Counting Null Values

- Count nulls per column:
  ```python
  df.isnull().sum()
  ```
  Example output: Physics=3, Chemistry=4, Maths=2, Computer=1.

- Count total nulls in whole DataFrame:
  ```python
  df.isnull().sum().sum()
  ```
  Example output: 10 (3+4+2+1).

---

## 3) Removing Nulls (Drop Methods)

### A) Drop Rows (default axis=0)
```python
df2 = df.dropna()
```
- Removes any row with at least one null.  
- Example: shape changed from (30,5) → (22,5).

### B) Drop Columns (axis=1)
```python
df3 = df.dropna(axis=1)
```
- Removes any column with at least one null.  
- Example: Only **Roll Number** remained (no nulls). Shape: (30,1).

### C) Control with `how`
- **`how='any'`** (default): drop row if **any** null exists.  
- **`how='all'`**: drop row only if **all** values are null.

### D) Modify Original with `inplace`
```python
df.dropna(inplace=True)
```
- Changes apply directly to `df`.  
- Example: df shape changed to (22,5).  
- No new DataFrame created, original overwritten.

---

## 4) Key Takeaways

- Use `df.isnull()` → detect nulls (True/False).  
- Use `df.isnull().sum()` → count per column.  
- Use `df.isnull().sum().sum()` → count total.  
- Use `dropna()` → remove rows/columns with nulls.  
- Control drop with **axis** (0=rows, 1=cols) and **how** (any/all).  
- Use `inplace=True` → modify the original DataFrame.  

---

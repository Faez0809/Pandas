# Pandas — Combining DataFrames with `concat()`  

This part covers the **`concat()` function**, which is now the preferred way to add one DataFrame below another (replacing the deprecated `append()`).

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

- `df1`: roll numbers 1–5  
- `df2`: roll numbers 6–10  
- Both have the same columns: Roll Number, Math, Physics  

---

## 2) Basic Concatenation

```python
df3 = pd.concat([df1, df2])
print(df3)
```

- Adds `df2` rows **after** `df1`.  
- Columns remain the same.  
- Order matters: `pd.concat([df2, df1])` reverses stacking.  

---

## 3) Important Parameters

### A) `ignore_index`

- **Default**: Keeps original indexes.  
  Example: 0–4 (df1) + 0–4 (df2).  
- **With ignore_index=True**: Creates continuous new index (0–9).  

```python
df3 = pd.concat([df1, df2], ignore_index=True)
print(df3)
```

### B) `sort`

- Sorts column names alphabetically when columns differ.  
- Example: Math, Physics, Roll Number.  

```python
df3 = pd.concat([df1, df2], sort=True)
print(df3)
```

---

## 4) Handling Non-Common Columns

If DataFrames have different columns:  
- Common columns keep values.  
- Missing values become NaN.  

Example:  

```python
df1 = pd.DataFrame({
    "Roll Number": [1, 2, 3],
    "Math": [50, 60, 70],
    "Chemistry": [55, 65, 75]
})

df2 = pd.DataFrame({
    "Roll Number": [4, 5, 6],
    "Math": [80, 90, 85],
    "Physics": [60, 70, 80]
})

df3 = pd.concat([df1, df2], ignore_index=True)
print(df3)
```

Output:  

```
   Roll Number  Math  Chemistry  Physics
0            1    50       55.0      NaN
1            2    60       65.0      NaN
2            3    70       75.0      NaN
3            4    80        NaN     60.0
4            5    90        NaN     70.0
5            6    85        NaN     80.0
```

---

## 5) Key Takeaways

- `append()` is **deprecated** → always use `pd.concat()`.  
- `concat()` stacks multiple DataFrames vertically (rows) or horizontally (columns).  
- Use `ignore_index=True` to reset index.  
- Use `sort=True` to order columns alphabetically.  
- Different columns → missing ones filled with NaN.  
- Simpler than `merge()` when you just want to **stack rows**.  

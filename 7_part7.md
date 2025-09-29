# Pandas — `loc()` and `iloc()` Functions 

This part covers **data access and filtering** using two key Pandas functions: `loc` and `iloc`.

---

## 1) Setup and Index Customization

```python
import pandas as pd

df = pd.read_csv("sample2.csv", index_col=1)
```
- The file has Roll Number, Section, Branch, Physics, Chemistry, Maths, Computer, DOB.  
- `index_col=1` → sets **Roll Number** as the DataFrame index.  
- Now rows are accessed by roll number instead of default 0,1,2...

---

## 2) The `loc()` Function (Label-Based)

### A) Access by Index Label
```python
df.loc[1]        # row with roll number 1
df.loc[5]        # row with roll number 5
df.loc[[1,5,7]]  # multiple rows
```

### B) Access Specific Columns
```python
df.loc[5, "Physics"]         # Physics marks of roll 5
df.loc[5:15, "Chemistry"]    # Chemistry marks from roll 5 to 15
```

### C) Conditional Filtering
```python
df.loc[df["Physics"] < 50]            # students with Physics < 50
df.loc[df["Physics"] > 80]            # students with Physics > 80
df.loc[df["Physics"] > 80, "Maths"]   # Maths marks of students with Physics > 80
```
- Conditions are the **most powerful use** of `loc()`.

---

## 3) The `iloc()` Function (Position-Based)

- Works with **row/column positions** (0-based), not labels.

### A) Access Rows by Position
```python
df.iloc[0]         # first row (position 0)
df.iloc[[0,2,4]]   # multiple rows by positions
```

### B) Access Columns by Position
```python
df.iloc[:, 0]   # all rows, first column (Section)
df.iloc[:, 1]   # all rows, second column (Branch)
```

### C) Slicing Rows and Columns
```python
df.iloc[0:5, 1]     # first 5 rows, column at index 1 (Branch)
df.iloc[0:5, 1:4]   # first 5 rows, columns 1-3 (Branch, Physics, Chemistry)
```

---

## 4) Key Differences

- `loc` → uses **labels** (row names, column names).  
- `iloc` → uses **positions** (0-based row/column numbers).  

---

## 5) Key Takeaways

- Use `loc` when you know the **labels**.  
- Use `iloc` when you want to select by **position**.  
- Both support single rows, multiple rows, columns, and slicing.  
- `loc` supports **conditions** (very powerful for filtering).  

---

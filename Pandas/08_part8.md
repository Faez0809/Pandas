# Pandas — `groupby()` and `merge()` Functions 

This part covers **organizing and combining data** using `groupby()` and `merge()`.

---

## 1) Setup

```python
import pandas as pd

df = pd.read_csv("engineering_data.csv")
```
Data has Section, Branch, Roll Number, and marks.

---

## 2) The `groupby()` Function (Aggregation)

### A) Group by One Column
```python
df.groupby("Branch")
```
- Groups rows by unique Branch values (CS, Electronics, Mechanical).  
- Each group contains the roll numbers and marks for that branch.

### B) Group by Multiple Columns
```python
df.groupby(["Branch", "Section"])
```
- Creates subgroups like:  
  - CS + Section A  
  - CS + Section B  
- Helps analyze data more specifically.

### C) Iterating Groups
```python
for name, group in df.groupby("Branch"):
    print(name)
    print(group)
```
- Loops through each group.  
- Prints group name + subgroup data.

---

## 3) The `merge()` Function (Combining DataFrames)

### A) Setup
Two DataFrames with Roll Numbers:
- `df1` has Period + Physics marks.  
- `df2` has Chemistry marks.  

### B) Default Merge = Inner Join
```python
pd.merge(df1, df2, on="Roll Number")
```
- Combines only rows where Roll Number exists in **both** DataFrames.  
- Example: Roll Numbers 1,2,3 kept if present in both.  
- Others are discarded.

### C) Outer Join
```python
pd.merge(df1, df2, on="Roll Number", how="outer")
```
- Combines **all rows** from both DataFrames.  
- If data is missing in one, NaN is placed.  
- Example: Roll Numbers 4,5 appear even if not in df1.

---

## 4) Key Takeaways

- `groupby()` → groups rows by one or more columns. Useful for subgroup analysis.  
- `merge()` → combines two DataFrames by a common column.  
- Default merge = **inner join** (common rows only).  
- Use `how="outer"` for **all rows**, with NaN for missing values.  

---

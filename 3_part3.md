# Pandas — DataFrame Functions 

These notes cover the **basic built-in functions** in Pandas to quickly check the structure and stats of a DataFrame.

---

## 1) Setup

```python
import pandas as pd

df = pd.read_csv("salarydata.csv")
```

- Reads the CSV into a DataFrame named `df`.  
- We then apply different functions to `df`.  

---

## 2) Functions for Data Dimensions and Structure

| Function | Purpose | Output Example |
|----------|----------|----------------|
| `df.columns` | Names of columns | Index(['years of experience', 'salary'], dtype='object') |
| `df.shape`   | Dimensions (rows, columns) | (30, 2) |
| `df.size`    | Total number of cells (rows × cols) | 60 |

---

## 3) Functions for Data Preview

### A) `df.head()`
- Shows the **first 5 rows** by default.  
- Pass a number to see more/less rows:  
  ```python
  df.head(2)   # first 2 rows
  ```

### B) `df.tail()`
- Shows the **last 5 rows** by default.  
- Pass a number for custom count:  
  ```python
  df.tail(8)   # last 8 rows
  ```

---

## 4) Functions for Info, Stats, and Nulls

### A) `df.describe()` — Statistics
- Works only on **numeric columns**.  
- Shows: count, mean, std, min, 25%, 50%, 75%, max.  
- Example: avg experience = **5.3 years**, avg salary = **$76,000**.

### B) `df.info()` — General Info
- Shows: number of entries, non-null values, data types.  
- Helps check for **missing values (nulls)**.  
- If non-null < total rows → dataset has missing values.

---

## 5) Example on Complex Data (Restaurant Dataset)

Suppose `df2` contains 250 rows × 9 columns.

1. **Preview:** `df2.head()` → quick look at rows and columns.  
2. **Shape:** `df2.shape` → (250, 9).  
3. **Info:** `df2.info()` → showed missing values in some columns (e.g., only 33 non-null values).  
4. **Describe:** `df2.describe()` → only for numeric columns (e.g., Rank, Sales, Units). Text columns are ignored.  

---

## 6) Key Takeaways

- Use **`df.head()` / `df.tail()`** → quick preview.  
- Use **`df.shape` / `df.size` / `df.columns`** → structure info.  
- Use **`df.describe()`** → numeric stats.  
- Use **`df.info()`** → data types + null check.  
- Together, these give a **clear picture of data** without deep analysis.

---

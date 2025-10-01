# Pandas — DataFrames and Reading External Files 

These notes focus on **theory**. Practical coding can be done in Colab.

---

## 1) What is a DataFrame?

- A **Series** is a simple **1-D array with labels**.  
- A **DataFrame** is a **2-D table** with **rows and columns**.  
- DataFrames are the main way to represent structured data in Pandas.  

Think of a DataFrame as an **Excel sheet in Python**.

---

## 2) Creating DataFrames Manually

General form:
```python
import pandas as pd
df = pd.DataFrame(data)
```

### A) Empty DataFrame
```python
df = pd.DataFrame()
```
- Creates an empty table with no rows and columns.

### B) From a List (Single Column)
```python
df = pd.DataFrame([10, 20, 30])
```
- Produces a DataFrame with **one column**.  
- Default row index = `0, 1, 2,...`.

### C) From List of Lists (Multiple Columns)
```python
df = pd.DataFrame([[1, "A"], [2, "B"], [3, "C"]])
```
- Each inner list = **one row**.  
- Columns are auto-numbered `0, 1, ...` unless we give names.

### D) From a Dictionary (Most Common)
```python
data = {
  "A": [1, 2, 3, 4, 5],
  "B": [10, 20, 30, 40, 50]
}
df = pd.DataFrame(data)
```
- Keys = **column names** ("A", "B").  
- Values (lists) = column data.  
- Row index = default `0,1,2,...` unless set manually.

---

## 3) Reading External Files

Most real datasets are stored in files (CSV, Excel).  
Instead of typing data by hand, we **load files directly**.

### A) Reading CSV Files
```python
df = pd.read_csv("file_path.csv")
```
- Needs the **full path** or relative path of the CSV file.  
- Returns a DataFrame with the file contents.

### B) Reading Excel Files (optional)
```python
df = pd.read_excel("file_path.xlsx")
```

### Example
Suppose a CSV file has:  
- **Years of Experience**  
- **Salary**  

After loading:
```python
df.head()
```
This shows the first few rows as a DataFrame.

---

## 4) Why DataFrames are Important

- Better for **structured data** than Series.  
- Handles **rows + columns** just like tables.  
- Can import from **CSV/Excel**, which is common in data analysis.  
- Easy to **filter, group, and analyze** later.  

---

## 5) Key Takeaways

- **Series** = 1-D (like one column).  
- **DataFrame** = 2-D (rows + columns).  
- Create DataFrames using **list, list of lists, or dict**.  
- Most often, you will **read CSV/Excel files** into DataFrames.  
- `pd.read_csv()` is one of the most used functions in Pandas.

---

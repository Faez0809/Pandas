# Pandas — Using the `replace()` Function 

This part covers the **`replace()` function**, which is used to substitute values in a DataFrame.

---

## 1) Setup

```python
import pandas as pd

df = pd.read_csv("sample.csv")
```

Data has roll numbers and subject marks.

---

## 2) Basic Replacement (Single Value)

```python
df2 = df.replace(26, 30)
```
- Replaces all 26 with 30 (in all columns).  
- Example: Chemistry value 26 → now 30; Math value 26 → now 30.

---

## 3) Replacement with Lists

### A) Many Old → One New
```python
df2 = df.replace([26, 36, 16], 99)
```
- Replaces 26, 36, 16 with 99 everywhere.

### B) Many Old → Many New (Paired)
```python
df2 = df.replace([26, 36, 16], [33, 15, 53])
```
- Matches by position:  
  - 26 → 33  
  - 36 → 15  
  - 16 → 53  

---

## 4) Column-Specific Replacement (Dictionary)

```python
df2 = df.replace({"Physics": {26: "ABCD"}})
```
- Only changes 26 → "ABCD" in **Physics** column.  
- Other columns remain unchanged.

---

## 5) Using Regular Expressions (Regex)

```python
df2 = df.replace(to_replace=r"\d{2}", value="ABCD", regex=True)
```
- Replaces all **two-digit numbers** with "ABCD".  
- `regex=True` enables pattern matching.

---

## 6) Permanent Change (inplace)

```python
df.replace(26, 30, inplace=True)
```
- Updates directly in `df`.  
- No need to assign to a new variable.

---

## 7) Key Takeaways

- `replace(old, new)` → simple replacement.  
- Lists allow replacing **multiple values** at once.  
- Dictionaries allow **column-specific** replacement.  
- Regex allows **pattern-based** replacement.  
- Use `inplace=True` for permanent changes.

---

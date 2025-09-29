# Pandas — Part 01 
---

## 1) What is Pandas?

- **Pandas** is a Python library for **data analysis** and **data manipulation**.
- It is **open source** and widely used.
- You usually import it as:
  ```python
  import pandas as pd
  ```


---

## 2) Series vs. Python List (Simple view)

**Series** = a **1‑D labeled array**.  
**List** = a simple Python sequence.

Why Series is often better than a list:
- Has **index labels** (auto or custom).
- Supports **vectorized math** and many built‑in methods.
- Handles **missing values** (like `NaN`) in a standard way.
- Works well with **DataFrame** (2‑D table) later.

> Important: A **Series is 1‑D**. It does **not** have multiple columns.  
> Multiple columns belong to a **DataFrame**.

---

## 3) Creating a Series

General form:
```python
pd.Series(data, index=None, dtype=None, name=None)
```

### A) From a list
```python
import pandas as pd

s = pd.Series([10, 20, 30])
# index: 0,1,2  | values: 10,20,30 | dtype inferred (e.g., int64)
```

- Default index starts at `0`.
- You can give a custom index:
  ```python
  s = pd.Series([10, 20, 30], index=[101, 102, 103], name="scores")
  ```
- Empty Series (default dtype is float64 in older versions):
  ```python
  empty = pd.Series([])              # dtype=float64 (legacy behavior)
  empty_i = pd.Series([], dtype=int) # set dtype explicitly
  ```

### B) Scalar value
- With only a scalar, you get **one value** at index `0`:
  ```python
  s = pd.Series(0.5)   # index: [0] -> 0.5
  ```
- To repeat the same value for many positions, pass an index list:
  ```python
  s = pd.Series(0.5, index=[1, 2, 3])  # 1->0.5, 2->0.5, 3->0.5
  ```

### C) From a dictionary
- **Keys** become the **index**; **values** become the data.
  ```python
  d = {"p": 1, "q": 2, "r": 3}
  s = pd.Series(d)  # index: p,q,r | values: 1,2,3
  ```

---

## 4) Access, Slicing, and Common Methods

### Access by label and position
```python
s["p"]     # label-based (index name)
s.loc["p"] # label-based (recommended)
s.iloc[0]  # position-based (first item)
```

### Slicing (end is **not** included)
```python
s.iloc[0:2]   # first two items by position
s.loc["p":"r"]  # label slice is inclusive when using labels
```

### Useful methods (quick idea)
```python
s.max()        # max value
s.min()        # min value
s.sum()        # sum of values
s.mean()       # average
s.unique()     # unique values (array)
s.value_counts()  # counts of each value
```

---

## 5) About “Multi‑Column” Data

If you need **multiple columns**, use a **DataFrame** (2‑D table).  
Example: a dictionary of lists becomes a DataFrame:

```python
data = {
  "Col1": [1, 2, 3, 4, 5],
  "Col2": [5, 6, 9, 4, 1],
  "Col3": [6, 7, 0, 5, 2]
}
df = pd.DataFrame(data)
```

|    | Col1 | Col2 | Col3 |
|----|------|------|------|
| 0  | 1    | 5    | 6    |
| 1  | 2    | 6    | 7    |
| 2  | 3    | 9    | 0    |
| 3  | 4    | 4    | 5    |
| 4  | 5    | 1    | 2    |

> Summary: **Series = 1 column (1‑D)**, **DataFrame = many columns (2‑D)**.

---

## 6) Key Takeaways (Quick)

- Pandas is for **analysis** and **manipulation** of data.
- **Series** is a labeled, 1‑D array with strong methods.
- Create Series from **list**, **scalar**, or **dict**.
- Use `.loc` (labels) and `.iloc` (positions) to access data.
- Use **DataFrame** when you want multiple columns.

---

## 7) Common Pitfalls

- Thinking a **Series** has “rows and columns”. It is **only 1‑D**.
- Forgetting that **label slicing** with `.loc` is **inclusive** on the end.
- Relying on default dtype for empty Series. Better to **set dtype**.
- Mixing `.loc` and `.iloc`. Keep them clear: labels vs positions.

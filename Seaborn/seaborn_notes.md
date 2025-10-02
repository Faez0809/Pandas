# Seaborn 

These notes explain **why** we use each Seaborn plot, **when** to use it, and what it tells us.   

---

## 0) What is Seaborn? Why use it?

- **Seaborn** is a Python library for **making charts**.  
- It is built on **Matplotlib**, but it makes things easier and prettier.  
- **Why use it?** Because it lets you quickly make **statistical plots** with very little code.  

Reminder code to start:
```python
import seaborn as sns
import matplotlib.pyplot as plt
sns.set_theme()
```

---

## 1) Two kinds of Seaborn functions

- **Axes-level**: like `sns.scatterplot`, `sns.lineplot`, `sns.histplot`.  
  → They make a single chart inside one set of axes. Use when you want **full control**.  

- **Figure-level**: like `sns.displot`, `sns.catplot`, `sns.relplot`.  
  → They can create **many small charts** automatically (facets). Use when you want to **compare groups side by side**.  

Example:
```python
sns.scatterplot(data=df, x="age", y="income")          # single chart
sns.displot(data=df, x="income", col="gender")         # one chart per gender
```

---

## 2) Understanding `hue`, `style`, and `size`

- These help you show **extra information** on the same chart.  
- **hue** = different colors for groups.  
- **style** = different line shapes or marker shapes.  
- **size** = different sizes of points.  

When to use:  
- Use `hue` if you want to **compare categories**.  
- Use `style` when printing in black & white or when color is not enough.  
- Use `size` for numeric differences, but be careful — too many sizes can confuse.  

Example:
```python
sns.lineplot(data=df, x="time", y="score", hue="group", style="phase")
```

---

## 3) Choosing the Right Plot (When and Why)

- **Scatter Plot (`sns.scatterplot`)**  
  - Shows relation between two numbers.  
  - Good for **finding patterns, clusters, or outliers**.  
  - Example: height vs weight.  

- **Line Plot (`sns.lineplot`)**  
  - Shows change over time or order.  
  - Good for **trends** (like sales each month).  

- **Histogram / KDE (`sns.histplot`, `sns.kdeplot`)**  
  - Shows how values are **distributed**.  
  - Good for **seeing shape**: normal, skewed, etc.  
  - KDE gives a smooth curve, histogram shows bars.  

- **Bar Plot (`sns.barplot`)**  
  - Compares group averages (or medians).  
  - Example: average marks of boys vs girls.  

- **Heatmap (`sns.heatmap`)**  
  - Shows **relationships in a table** with color.  
  - Example: correlation between subjects (Math, Physics, English).  

- **Pair Plot (`sns.pairplot`)**  
  - Shows many scatterplots together.  
  - Good for quickly checking **relationships** between many columns.  

---

## 4) Colors and Palettes (Why they matter)

- Colors help us **see groups quickly**.  
- Use the right type:  
  - **Qualitative (categories):** deep, muted, pastel, bright.  
  - **Sequential (low→high numbers):** viridis, magma, flare.  
  - **Diverging (negative vs positive):** coolwarm, RdBu.  

Example:
```python
sns.set_theme(palette="pastel")
```

---

## 5) Showing Uncertainty (Error Bars)

- Averages can hide variation.  
- Seaborn shows **error bars** by default (like ± standard deviation or percentile).  
- In new versions, use `errorbar=` instead of old `ci=`.  

Example:
```python
sns.barplot(data=df, x="day", y="tip", errorbar=("pi", 95))
```

---

## 6) Facets (Small Multiples)

- Faceting = splitting data into many smaller charts.  
- Why? Easier to compare groups side by side.  
- When to use: when you have categories like gender, region, year.  

Example:
```python
sns.displot(data=df, x="income", col="gender", row="region")
```

---

## 7) Pairplot (More Details)

- Use pairplot when you want to see **all relationships at once**.  
- **hue**: separate by a group (like species of penguins).  
- **corner=True**: removes duplicate plots, easier to read.  
- **kind="hist"**: shows histograms on diagonals.  
- **markers**: different shapes for each group (helpful for colorblind).  

Example:
```python
sns.pairplot(penguins, hue="species", corner=True, markers=["o","s","D"])
```

---

## 8) Heatmaps (More Details)

- Use for **correlation matrices**.  
- Dark/light colors = weak/strong relationships.  
- `center=0` is useful for showing negative vs positive values.  

Example:
```python
corr = df.corr(numeric_only=True)
sns.heatmap(corr, annot=True, fmt=".2f", cmap="YlGnBu", center=0)
```

---

## 9) Common Updates (Important!)

- Old: `sns.distplot` → New: `sns.histplot` / `sns.kdeplot` / `sns.displot`.  
- Old: `ci=` → New: `errorbar=`.  
- Old: Pandas `append()` → New: `pd.concat([...])`.  

---

## 10) Always Add Context

- **Titles** and **labels** tell the story.  
- Plots without words are confusing.  
- Good habit: one clear sentence in the title.  

Example:
```python
plt.title("Boys scored higher in Math, but Girls scored higher in Physics")
plt.xlabel("Subjects")
plt.ylabel("Average Marks")
```

---

### Quick Cheat Sheet
- Scatter: relation → `sns.scatterplot(x, y)`  
- Line: trend → `sns.lineplot(x, y)`  
- Hist/KDE: distribution → `sns.histplot(x, bins=30, kde=True)`  
- Bar: compare groups → `sns.barplot(x, y)`  
- Heatmap: matrix → `sns.heatmap(corr, annot=True)`  
- Pairplot: many relations → `sns.pairplot(df, hue=...)`  

---

**Main Idea:** Don’t just plot — **ask a question first**. Then choose the plot that answers it clearly.

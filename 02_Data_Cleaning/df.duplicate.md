## Checking for Duplicate Rows in a Dataset using Python

You can check for duplicate rows in a dataset using **pandas** in Python. Here are different ways to do it:

### 1. Using `duplicated()` Method
The `duplicated()` function returns a boolean Series where **True** indicates that the row is a duplicate.

```python
import pandas as pd

# Sample DataFrame
data = {'A': [1, 2, 2, 4, 5, 2],
        'B': [10, 20, 20, 40, 50, 20],
        'C': [100, 200, 200, 400, 500, 200]}

df = pd.DataFrame(data)

# Find duplicate rows
duplicate_rows = df[df.duplicated()]
print(duplicate_rows)
```

🔹 **By default, `duplicated()` checks all columns.**  
🔹 **Only the second (and later) occurrence of a duplicate row is marked as `True`.**

---

### 2. Using `duplicated(keep=False)` to Mark All Duplicates
If you want **all occurrences** of duplicates (including the first one), use `keep=False`:

```python
df[df.duplicated(keep=False)]
```

---

### 3. Finding Duplicates in Specific Columns
To check for duplicates based on selected columns:

```python
df[df.duplicated(subset=['A', 'B'])]
```

---

### 4. Counting the Number of Duplicate Rows
```python
df.duplicated().sum()  # Count duplicate rows
```

---

### 5. Getting Unique Duplicate Rows
To get only the **unique** rows that are duplicated (without repetitions):

```python
df[df.duplicated(keep=False)].drop_duplicates()
```


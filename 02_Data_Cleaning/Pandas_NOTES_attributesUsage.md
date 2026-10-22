# Pandas Attributes and Their Usage

This guide explains which attributes or fields work with **DataFrame**, **Series**, and **Index** objects in Pandas, as well as attributes for **NumPy arrays**.

---

## **1. DataFrame Attributes/Fields**
These attributes are specific to **DataFrame** objects:

| **Attribute**       | **Description**                                                                                      |
|---------------------|------------------------------------------------------------------------------------------------------|
| `columns`           | Returns the column labels as an `Index` object.                                                     |
| `index`             | Returns the row labels as an `Index` object.                                                        |
| `dtypes`            | Returns the data types of each column as a Series.                                                  |
| `shape`             | Returns a tuple representing the dimensions of the DataFrame (rows, columns).                       |
| `size`              | Returns the total number of elements in the DataFrame.                                              |
| `values`            | Returns the underlying data as a NumPy array.                                                       |
| `axes`              | Returns a list containing the row and column labels as `Index` objects.                             |
| `ndim`              | Returns the number of dimensions (2 for a DataFrame).                                               |
| `empty`             | Returns `True` if the DataFrame is empty.                                                           |
| `T` (transpose)     | Returns the transposed version of the DataFrame.                                                    |

---

## **2. Series Attributes/Fields**
These attributes are specific to **Series** objects:

| **Attribute**       | **Description**                                                                                      |
|---------------------|------------------------------------------------------------------------------------------------------|
| `index`             | Returns the row labels (index) as an `Index` object.                                                |
| `values`            | Returns the underlying data as a NumPy array.                                                       |
| `dtype`             | Returns the data type of the Series.                                                                |
| `shape`             | Returns the shape of the Series as a tuple (number of rows,).                                       |
| `size`              | Returns the number of elements in the Series.                                                       |
| `ndim`              | Returns the number of dimensions (1 for a Series).                                                  |
| `empty`             | Returns `True` if the Series is empty.                                                              |
| `name`              | Returns or sets the name of the Series.                                                             |
| `T`                 | Returns the transposed version of the Series (no effect, as Series are 1D).                         |

---

## **3. Index Attributes/Fields**
These attributes are specific to **Index** objects, which are used for row or column labels:

| **Attribute**       | **Description**                                                                                      |
|---------------------|------------------------------------------------------------------------------------------------------|
| `values`            | Returns the underlying data as a NumPy array.                                                       |
| `dtype`             | Returns the data type of the index.                                                                 |
| `shape`             | Returns the shape of the Index as a tuple.                                                          |
| `size`              | Returns the number of elements in the Index.                                                        |
| `ndim`              | Returns the number of dimensions (1 for Index).                                                     |
| `empty`             | Returns `True` if the Index is empty.                                                               |
| `is_unique`         | Returns `True` if the labels in the Index are unique.                                               |
| `name`              | Returns or sets the name of the Index.                                                              |
| `T`                 | Returns the transposed version of the Index (no effect, as Index is 1D).                            |

---

## **4. NumPy Array Attributes**
These attributes are specific to **NumPy arrays**:

| **Attribute**       | **Description**                                                                                      |
|---------------------|------------------------------------------------------------------------------------------------------|
| `shape`             | Returns the dimensions of the array as a tuple.                                                     |
| `size`              | Returns the total number of elements in the array.                                                  |
| `dtype`             | Returns the data type of the elements in the array.                                                 |
| `ndim`              | Returns the number of dimensions of the array.                                                      |
| `T`                 | Returns the transposed array (for 2D arrays and higher).                                             |
| `data`              | Returns a buffer containing the actual elements of the array.                                       |
| `strides`           | Returns a tuple of bytes to step in each dimension when traversing the array.                        |
| `nbytes`            | Returns the total number of bytes consumed by the elements of the array.                            |
| `itemsize`          | Returns the size of one element in the array in bytes.                                              |
| `base`              | Returns the base object if the array is a view of another array.                                    |
| `flags`             | Returns information about the memory layout of the array.                                           |
| `real`              | Returns the real part of the array elements (for complex arrays).                                   |
| `imag`              | Returns the imaginary part of the array elements (for complex arrays).                              |

---

## **Differences Between DataFrame, Series, Index, and NumPy Array**
1. **DataFrame**:
   - Has both `index` (rows) and `columns` (column labels).
   - Works with tabular, structured data.

2. **Series**:
   - Only has `index` (row labels) but no `columns` attribute because it's 1D.

3. **Index**:
   - Used for both row labels and column labels. It doesn't contain actual data.

4. **NumPy Array**:
   - Works with n-dimensional data (not just 1D or 2D).
   - Does not have `index` or `columns` attributes.

---

## **Common Attributes Across All Four Objects**
| **Attribute** | **Description**                             |
|---------------|---------------------------------------------|
| `values`      | Returns the data as a NumPy array.          |
| `dtype`       | Returns the data type of the object.        |
| `shape`       | Returns the shape of the object.            |
| `size`        | Returns the total number of elements.       |
| `ndim`        | Returns the number of dimensions.           |
| `T`           | Transposes the object (no effect for 1D).   |

---

## **Example Code**
```python
import pandas as pd
import numpy as np

# Sample DataFrame
data = {
    "Name": ["Alice", "Bob", None],
    "Age": [25, None, 30],
    "City": ["New York", "Los Angeles", None]
}
df = pd.DataFrame(data)

# DataFrame Attributes
print("DataFrame Columns:", df.columns)  # Index(['Name', 'Age', 'City'], dtype='object')
print("DataFrame Index:", df.index)      # RangeIndex(start=0, stop=3, step=1)
print("DataFrame Shape:", df.shape)      # (3, 3)

# Series Attributes
print("\nSeries Index:", df["Name"].index)  # RangeIndex(start=0, stop=3, step=1)
print("Series Values:", df["Name"].values)  # ['Alice' 'Bob' None]

# Index Attributes
index = df.columns
print("\nIndex Values:", index.values)      # ['Name' 'Age' 'City']
print("Index Size:", index.size)            # 3

# NumPy Array Example
array = np.array([[1, 2, 3], [4, 5, 6]])
print("\nArray Shape:", array.shape)        # (2, 3)
print("Array Size:", array.size)            # 6
print("Array Dtype:", array.dtype)          # int64 (or platform-specific integer type)
```

---

By understanding these attributes, you can use the right one for the right object and avoid errors like trying to access `columns` on a Series or NumPy array.

---
title: Introduction to Data Science in Python - Week 2 Course Notes
date: "2022-01-15T12:12:03.284Z"
description: "Covers basic data processing with Pandas: reading data into a DataFrame and querying data in a DataFrame."
---

[Ref: Coursera - Introduction to Data Science in Python](https://www.coursera.org/learn/python-data-analysis)

### Series Data Structure
Series can be thought of a cross between a list and a dictionary. The items are **stored in an order** and there are labels with which data can be retrieved.

A Series would be two columns of data wherein, the first is a special index (similar to keys in a dictionary) and the second is for data. Note that the data column has it's own label and can be retrieved using a ```.name``` attribute. Series can be handy when merging multiple columns of data.

Example below uses a list of strings to create a Pandas Series. The resulting Series has a data type of ```object```.
```python
import pandas as pd
letters = ['Z', 'Y', 'X']
pd.Series(letters)

# 0    Z
# 1    Y
# 2    X
# dtype: object
```

Using a list of integers to create a Pandas Series. The resulting Series has a data type of int64.
```python
nums = [22, 11, 99]
pd.Series(nums)

# 0    22
# 1    11
# 2    99
# dtype: int64
```

```python
letters = ['Z', 'X', None]
pd.Series(letters)

# 0       Z
# 1       X
# 2    None
# dtype: object
```

Pandas represents ```NaN``` as a floating point number and rest of the values are type casted to floating point numbers.
```python
nums = [1, 2, None]
pd.Series(nums)
# 0    1.0
# 1    2.0
# 2    NaN
# dtype: float64
```

```NaN``` is not equivalent to ```None```
```python
np.nan == np.nan # false
```

Use the following to test for the presence of not a number.
```python
np.isnan(np.nan) # True
```

Using a dictionary object to create a Pandas Series.
```python
letter_pts = { 'A': 10, 'B': 8, 'C': 6}
s = pd.Series(letter_pts)
s.index
# Index(['A', 'B', 'C'], dtype='object')
```

Using a list of tuples to create a Pandas Series object.
```python
list_tuples = [('A', '1'), ('C', '3')]
pd.Series(list_tuples)

# 0    (A, 1)
# 1    (C, 3)
# dtype: object
```

An index can also be provided as a list for creating a Series.
```python
grade_pt_series = pd.Series([10,8,6], index=['a', 'b','c'])
grade_pt_series
# a    10
# b     8
# c     6
# dtype: int64
```

```NaN``` is returned when the given index doesn't have a corresponding value in the Series
```python
game_scores = { 'Bob': 99, 'Jane': 22, 'Jade': 6}
s = pd.Series(game_scores, index=['Bob', 'Jane', 'Zen'])
s
# Bob     99.0
# Jane    22.0
# Zen      NaN
# dtype: float64
```
### Quering a Series
A Pandas series can be queried either by an index position or an index label.
- ```iloc``` attribute can be used to query by a numeric location.
- ```loc``` attribute can be used to query by an index label.

Note that ```iloc``` and ```loc``` are attributes and not methods.

Iterating through a Pandas Series to obtain total sum.
```python
nums_series = pd.Series([10, 20, 30])
total = 0
for num in nums_series:
    total += num
total # 60
```

Using numpy to find the total sum of a Series.
```python
num_series = pd.Series([10, 20, 30])
np.sum(num_series) #60.0
```
To evaluate the performance difference between using a basic for loop versus using numpy's builtin methods, the ```timeit``` magic method can be used.

```python
%%timeit -n 100
rand_nums = pd.Series(np.random.randint(0, 1000, 10000))
total = 0
for num in rand_nums:
    total += num
total/len(rand_nums)
# 1.25 ms ± 6.44 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)
```

```python
%%timeit -n 100
rand_nums = pd.Series(np.random.randint(0, 1000, 10000))
# generate: 10K random nums between 0 and 1000
total = np.sum(rand_nums)
total / len(rand_nums) # average
# 229 µs ± 16.7 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)
```

### DataFrame Data Structure

### DataFrame Indexing and Loading

### Querying a DataFrame

### Missing Values

### Manipulating a DataFrame

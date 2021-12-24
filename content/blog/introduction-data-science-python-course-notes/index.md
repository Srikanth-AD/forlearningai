---
title: Introduction to Data Science in Python - Course Notes
date: "2021-12-24T13:12:03.284Z"
description: "Introduction to Data Science in Python - course notes.
Covers fundamentals of Python, data manipulation, processing and cleanup with Numpy and Pandas."
---

[Ref: Coursera - Introduction to Data Science in Python](https://www.coursera.org/learn/python-data-analysis)

## Python: Types and Sequences

**Common types**: string, None, int, float, function

**Type** function: can be used to identify the type of a given reference.

```python
type('string') # str
type(None) # NoneType
type(add_nums) # function
type((100,200)) # tuple
```

### Tuples, Lists, Dictionaries

**Tuples**: immutable, items are ordered and cannot be changed once created.
```python
sample_tuple=(101,'x',22, 'y')
```

**Lists**: mutable, the number of elements and element values can be changed.
```python
sample_list=[200,'w',99, 'v']
sample_list.append(300)
```

Lists and tuples are iterable types.
```python
for item in sample_list:
    print(item)
```

```python
i = 0
while (i != len(sample_list))
    print(sample_list[i])
    i = i + 1
```

**in operator**
```python
20 in [20,33] # True
```

### Slicing
```python
sample_string = 'Sample String'
print(x[:3]) # Sam
print(x[-1]) # g
```

**Split function**: breaks a string up based on a given pattern
```python
fname = 'Jane'
lname = 'Doe'
print(fname + ' ' + lname) # Jane Doe
print(fname.split('')) # ['J', 'a', 'n', 'e']
print(fname.split('')[-1]) # 'e'
```
**Dictionaries**: labelled collections which don't have an order. For each value inserted into the dictionary, a key would be needed to fetch the corresponding value.

```python
sample_dict={'Chris': 'c@j.com', 'Brook': 'b@k.com'}
sample_dict['Chris'] # 'c@j.com'
```

Iterate over keys and values using the ```items()``` function.
```python
for name, email in sample_dict.items():
    print(name, email)
```

**Unpacking values**
```python
 my_tuple = ('John', 'Doe', 30)
 fname, lname, age = my_tuple
```
**Python string formatting**
```python
order_details = {'order_id': 'o123', 'order_total': '22.20'}
order_statement = 'Order number: {} has a total of ${}'
print(order_statement.format(order_details['order_id'], order_details['order_total']))
# Order number: o123 has a total of $22.20
```

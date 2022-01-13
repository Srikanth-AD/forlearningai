---
title: Introduction to Data Science in Python - Course Notes
date: "2021-12-24T13:12:03.284Z"
description: "Introduction to Data Science in Python - course notes.
Covers fundamentals of Python, data manipulation, processing and cleanup with Numpy and Pandas."
---

[Ref: Coursera - Introduction to Data Science in Python](https://www.coursera.org/learn/python-data-analysis)

### Python: Types and Sequences

**Common types**: string, None, int, float, function

**Type** function: can be used to identify the type of a given reference.

```python
type('string') # str
type(None) # NoneType
type(add_nums) # function
type((100,200)) # tuple
```

#### Tuples, Lists, Dictionaries

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

#### Slicing
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

**Dates and Times**
Get current time since the epoch using the ```time``` module.
```python
import datetime as dt
import time as tm
tm.time() # seconds from epoch
dtnow = dt.datetime.fromtimestamp(tm.time())
dtnow # datetime.datetime(2021, 10, 10, 10, 10, 50, 50071)
```

#### Python Objects, map()

**Classes**: generally named in camelcase. Class variables can be declared and are shared across all instances.

Objects in Python don't have private and public methods. Constructors are optional.
```python
class Person:

    def set_age(self, new_age):
        self.age = new_age

p1 = Person()
p1.set_age(22)
```

```map()``` function takes two parameters: a function that's to be executed and, an iterable to which the function is applied to every item in the iterable. Maps are iterable, just like lists.
```map()``` returns a map object.

[Lazy evaluation](https://towardsdatascience.com/what-is-lazy-evaluation-in-python-9efb1d3bfed0) is used here. The expression is not immediately evaluated. It is only evaluated when the outcome is needed. This programming design makes it memory and time efficient.

```python
nums1 = [9, 2, 10]
nums2 = [7, 8, 2]
lowest = map(min, nums1, nums2)
lowest # map object
```

Another example of lazy evaluation is the ```range()``` function. ```range(3)``` only stores the start, stop, step values and calculates each item when it's needed.
```python
 sys.getsizeof(range(5)) # 48
 sys.getsizeof(range(500)) # 48
```
```getsizeof()``` returns the size of an object in bytes.

Other examples of lazy evaluation include: zip, generators and decorators.

**Lambdas**: Lambdas are anonymous functions. Return of a Lambda is a function reference. Default values aren't allowed for Lambda parameters.

```python
x = lambda a,b,c : a * b * c
print (x(1,2,3)) # 6
```

**List Comprehension**: condensed format. May offer readability and performance benefits.
```python
sample_list = [i for i in range(0,3) if i % 2 == 0] # [0, 2]

my_list = [i*j for i in range(10) for j in range(10)] # [0, 0, 0, 0, 1, 2, 0, 2, 4]
```

### Data Manipulation: Numpy and Regex

#### Numpy - Array Creation
One way to create an Array is to pass a list or list of lists as an argument to a numpy array.

```python
a = np.array([3,4,5])
print(a.ndim) # Prints number of dimensions of a list

b = np.array([3,4,5], [13,14,15])
print(b.shape) # Shape - returns a tuple indicating the length of each dimension
print(b.dtype) # dtype('int64')
```
Data within Numpy arrays is homogeneous.  

Some helper functions to create Numpy arrays with initial placeholders.
```python
d = np.zeros((2,3)) #2,3 is the shape
print(d)

e = np.ones((3,3))
print(e)

f = np.arange(10, 50, 2) # parameters: start, end (exclusive) and step
```

#### Array Operations

Array operators are applied element-wise.

**Boolean array**: apply an operator on an array and a boolean is returned for any element in the original.
True is emitted, if the condition is met.

```python
a = np.array([5, 10, 15])
b = np.array([1, 2, 3])
print(a - b) # [4, 8, 12]
print(a * b)

farenheit = np.array([0, -10, 15])
celcius = (farenheit - 31) * (5/9)
celcius%2 == 0 # returns boolean array
```
**Matrix manipulation**:

- * is for element-wise comparison
- @ sign is used for dot product

```python
a = np.array([[2,2], [0,1]])
b = np.array([[2,2], [0,1]])

print(a*b)
print(a@b)
```
**Upcasting**: when manipulating arrays of different types, the more general of the two types is used for the resulting array.

#### Indexing, Slicing and Iterating

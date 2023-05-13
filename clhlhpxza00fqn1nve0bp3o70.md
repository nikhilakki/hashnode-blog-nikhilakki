---
title: "Map, Zip & Filter | Understanding Python built-in functions."
datePublished: Sat May 13 2023 04:31:39 GMT+0000 (Coordinated Universal Time)
cuid: clhlhpxza00fqn1nve0bp3o70
slug: map-zip-filter-understanding-python-built-in-functions
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680974545680/ef76d732-076d-43bd-a8d0-bd124d2e7b13.png
tags: python, map, filter, zip, built-in-functions

---

In Python, `map()`, `zip()`, and `filter()` are built-in functions that are used to perform different operations on iterables like lists, tuples, and sets.

1. `map()` **function:** This function applies a given function to each item of an iterable and returns a new iterable with the results.
    

Syntax: `map(function, iterable)`

Example:

```python
# Convert Celsius to Fahrenheit
celsius = [39.2, 36.5, 37.3, 37.8]
fahrenheit = list(map(lambda x: (9/5)*x + 32, celsius))
print(fahrenheit)
```

Output:

```bash
[102.56, 97.7, 99.14, 100.03999999999999]
```

1. `zip()` **function:** This function takes one or more iterables and aggregates them into a single iterable of tuples.
    

Syntax: `zip(*iterables)`

Example:

```python
# Merge two lists
list1 = [1, 2, 3]
list2 = ['a', 'b', 'c']
merged_list = list(zip(list1, list2))
print(merged_list)
```

Output:

```bash
[(1, 'a'), (2, 'b'), (3, 'c')]
```

1. `filter()` **function:** This function applies a given function to each item of an iterable and returns a new iterable with the items for which the function returns True.
    

Syntax: `filter(function, iterable)`

Example:

```python
# Find all even numbers in a list
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)
```

Output:

```bash
[2, 4, 6, 8, 10]
```

### **Summary**

Here are some key takeaways about `map()`, `zip()`, and `filter()` functions in Python:

1. `map()` is a built-in function that applies a given function to each item of an iterable and returns a new iterable with the results.
    
2. `zip()` is a built-in function that aggregates one or more iterables into a single iterable of tuples.
    
3. `filter()` is a built-in function that applies a given function to each item of an iterable and returns a new iterable with the items for which the function returns True.
    
4. These functions can be used to simplify code and make it more concise.
    
5. These functions can be used to perform common data manipulation tasks, such as converting units of measurement, merging data from multiple sources, and filtering data based on specific criteria.
    
6. These functions are often used in combination with lambda functions to perform simple operations on iterables.
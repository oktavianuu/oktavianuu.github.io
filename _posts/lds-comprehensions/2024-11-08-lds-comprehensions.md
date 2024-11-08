---
title: List, Dictionary and Set Comprehensions
date: 2024-11-08 08:55:00 +07:00
modified:
tags: [programming, list, dictionary, set, comprehensions]
description:
---
I wrote this article to better understand list comprehensions. In this writing I'll explain the concept as simple as possible as if I'm explaining it to a toddler. As Enstein said that "_**if you can't explain it to a six years old, you don't understand it yourself**_." Moreover, I use the learning method from Feynman that we must teach a concept to a toddler, review and simplify it to better understand a concept.

#### List Comprehensions
Enough for the introduction, now what is **list comprehension**?
In Python, it is a feature that is widely used by programmer, data scientista and people who use Python in their job. List comprehension allows us to briefly form a new list by filtering elements of a collection and transforming the elements passing into one brief expression and then return the result. In other words, list comprehension provides a very compact way to process part or entire element of a list and return a list as a result. The skeleton of list comprehension as follow:
```python
list_comp = [expr for value in collection if condition]
```
- **expr**: the expression to evaluate and include in the new list. 
- **value**: The variable that takes the value of the current element in the collection.
- **collection**: the collection we're iterating over.
- **condition**: this is optional condition to filter items/ elements of the list.

The list comprehension above is equivalent to the following `for` loop:
```python
result = []
for value in collection:
    if condition:
        result.append(value)
```
To better understand this concept, here is the implementation of the list comprehension:
```python
strings = ["a", "as", "bat", "car", "dove", "lion"]

result = [x.upper() for x in strings if len(x)>2]
```
In the above example, we're making a new list based on the list of `strings`. Our objective is to filter elements which has length more than 2 and assign them to a new list named `result`. The `x.upper()` means that the element will be converted to uppercase. The resul of the list comprehension is:
```python
['BAT', 'CAR', 'DOVE', 'LION']
```
Everytime we apply list comprehension, the rules are the same. The only difference lies on the expression and the condition we want to apply. 

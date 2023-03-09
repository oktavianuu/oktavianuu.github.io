---
title: How to Write Effective Program
date: 2023-03-09 09:15:00 +07:00
modified: 
description:
image:
---
When writing a program, there are some factors we must take into consideration, for example are computer power and the speed of execution of the program itself. Let's take a look at the simple program below for finding the largest number from a list:
```python
my_list = [17, 3, 11, 5, 1, 9, 7, 15, 13]
largest = my_list[0]

for i in my_list:
    if i > largest:
        largest = i

print(largest)

# The code above gives us 17 as the output.
```
Okay, the answer is correct. If you run the program it will gives you ```17``` as the output. So what is the problem here? 
Well, the program above performs one unnecessary comparison. When we run the program, at first iteration, the first element will be compared to itself. Even the output is correct, but when we talk about computing power and the speed of execution, this comes into account. We need to find new algorithm so tolve the problem. We can solve the problem by slicing. Look at the code snippet below:
```python
my_list = [17, 3, 11, 5, 1, 9, 7, 15, 13]
largest = my_list[0]

for i in my_list[1:]:
    if i > largest:
        largest = i

print(largest)
```
Now we have a better algorithm to find the largest number from my_list variabel. We exclude the first element from being compared to itself. We only compare the first element with the rest of the element excluding element number 1 (or element at index 0). 
---
title: Algorithm for noob
date: 2024-09-27 11:19:00 +07:00
modified: 
tags: [algorithm]
description: 
---
## What is Algorithm?
Simply, algorithm is a procedure to accomplish a specific task. It solves general, _well-specified_ problem. To make it clear, consider the following problem known as sorting:

_Problem_: Sorting
_Input_: A sequence S of n keys a~1~, . . . , a~n~. 
_Output_: The permutation (reordering) of the input sequence such that a^'^~1~ $\ge$ a^'^~2~ $\ge$ . . . $\ge$ a^'^~n-1~ $\ge$ a^'^~n~.

In _sorting_ problem, the instance of a problem might be an array of strings or numbers e.g. [97, 63, 134, 207, 194, 150]. So, to be specific, an algorithm is a procedure that takes any possible input of instances and transforms it to the desired result or output. If you google or ask any sophisticated AI chat-based application about how to solve a sorting problem, there are many different algorithms to solve _sorting_  problem, one of them is **insertion sort**. It is an algorithm that works by interatively inserting each element of an unsorted list into its correct position in a sorted portion of a list. It is much less effiecient on largest list compared to other advanced algorithms such as _quicksort, heapsort_, or _merge sort_.
The implementation of _insertion sort_ can be seen as follow (implemented in C):
```c
insertion_sort(item s[], int n)
{
    int i, j;   /* counters */

    for (i=1; i<n; i++) {
        j=i;
        while ((j>0) && (s[j] < s[j-1])) {
            swap(&s[j], &s[j-1]);
            j = j-1;
        }
    }
}
```
We can ignore the details about the C language here as it is not the main intention of this writing to learn a programing language. The code shows how to implement insertion sort in C.

When we think about algorithm, what comes to mind is "**what makes an algorithm good?**" There are three properties of a good algorithm, they are _correctness_, _effectiveness_ and _easiness_ of its implementation. 
---
title: Algorithm for noob
date: 2024-09-27 11:19:00 +07:00
modified: 
tags: [algorithm]
description: 
---
<script type="text/javascript" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
</script>

## What is Algorithm?
Simply, algorithm is a procedure to accomplish a specific task. It solves general, _well-specified_ problem. To make it clear, consider the following problem known as sorting:

_Problem_: Sorting<br>
_Input_: A sequence S of n keys $$a_1, . . . , a_n$$.<br> 
_Output_: The permutation (reordering) of the input sequence such that $$a'_1 \geq a'_2 \geq . . . \geq a'_{n-1} \geq a'_n$$.

In _sorting_ problem, the instance of a problem might be an array of strings or numbers e.g. `[97, 63, 134, 207, 194, 150]`. To be specific, an algorithm is a procedure that takes any possible input of instances and transforms it to the desired result or output. If you google or ask any sophisticated AI chat-based application about how to solve a sorting problem, there will be many different algorithms to solve _sorting_  problem, one of them is **insertion sort**. It is an algorithm that works by iteratively inserting each element of an unsorted list into its correct position in a sorted portion of a list. It is much less effiecient on largest list compared to other advanced algorithms such as _quicksort, heapsort_, or _merge sort_, but advanced algorithms aren't needed for starters. What is more important is the basic principle of it.  Algorithm is a procedure, it must be looked a process to achieve something. Step by step and clear. It is more like _how to do_ something **correctly** and **efficiently**. Back to the _insertion sort_ again, how do we sort an array of elements or number from the smallest to the largest? We just need to compare each element and sort them. Programmatically we can sort a list of number with the following procedure:
list of number need to be sorted = `97, 63, 134, 207, 194, 150`
1. Compare the second element with the previous element,
2. Place the smaller element at the first index of the list,
3. Compare the the next elements to the previous element,
4. If the preceding element is bigger, shift its position.

We need to translate our way of sorting list into `pseudo-code` as follows:
Abstract `Pseudo Code`:
```sql
procedure insertion_sort(list, n)
    for each element from the second to the last in list do
        compare element with the previous elements
        shift elements to the right until the correct position is found
        insert element in the correct position
    end for
end procedure
```
In the pseudo code above, the name of our procedure is `insertion_sort`. Inside the procedure, the comparing and shifting processess are done iteratively until all elements reordered ascendingly. Here, the algorithm is written with high level of abstraction so that it will be easy for any human to understand it. It focuses on what the algorithm does rather than how it does it. This pseudo-code is useful for high-level understanding, focusing on the concept without specifying the details of the comparison and swapping process. Since we are going to make our computer understand the algorithm, we still need to translate it to a lower level of abstraction so that it will be close to its actual implementation.

Low-Level `Pseudo Code`:
```c
procedure insertion_sort(s, n)
    for i from 1 to n-1 do
        j = i
        while j > 0 and s[j] < s[j-1] do
            swap(s[j], s[j-1])
            j = j - 1
        end while
    end for
end procedure
```
This version is more detailed and clearly descibes how the algorithm works step by step, making it closer to its actual implementation. Here is how it works:
- The name our procedure is `insertion_sort`,
- `For i from 1 to n-1`: This shows that the outer loop starts from the second element (index 1) and iterates through the entire list,
- `j = i`: This indicates the current element to be sorted, starting with index i.
- `While j > 0 and s[j] < s[j-1]`: This condition compares the current element `s[j]` with the previous element `s[j-1]`. If the current element is smaller, the while loop continues swapping it with previous elements to insert it into the correct position.
`swap(s[j], s[j-1])`: This is the concrete operation that moves elements to the right by swapping. We hide the details how this function works.
- `j = j - 1`: After a swap, j is decremented, moving the comparison to the previous element.

This version breaks down the process of sorting, showing explicitly the comparison, the swapping, and how the elements are moved one by one.

We can now implement our _sorting_ algorithm in a programming language, in this case C. 

Insertion sort implemented in C:
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
This algorithm is applicable to any programming language. Below is the same sorting algorithm, implemented in python.
```python
def insertion_sort(s):
    n = len(s) # Get the number of elements in the list

    for i in range(1, n):
        j = i
        while j > 0 and s[j] < s[j - 1]: 
            # swap elements
            s[j], s[j-1] = s[j-1], s[j]
            j -= 1
```

That is how algorithm works and how we create it from scratch. We can ignore the details about the `C` or `python` language here as it is not the main intention of this writing to learn a programing language. The code shows how to implement insertion sort in C and python. 

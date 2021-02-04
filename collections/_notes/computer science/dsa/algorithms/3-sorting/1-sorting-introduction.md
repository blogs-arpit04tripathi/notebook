---
layout: post
title: Sorting Introduction
permalink: /algorithms/sorting/introduction
---

- Sorting refers to arranging data in a particular order.
- Data searching can be optimized to a very high level, if data is stored in a sorted manner. 

|In-Place Sorting	|Not-In-Place Sorting|
|---|---|
Sorting algorithms may require some extra space for comparison and temporary storage of few data elements. These algorithms do not require any extra space and sorting is said to happen in-place, or for example, within the array itself. This is called in-place sorting. |In some sorting algorithms, the program requires space which is more than or equal to the elements being sorted. Sorting which uses equal or more space is called not-in-place sorting. 
|Bubble sort is an example of in-place sorting.	|Merge-sort is an example of not-in-place sorting.|

Stable Sorting and Not Stable Sorting – In a Sorting Algorithm, after sorting the contents, does not change the sequence of similar content in which they appear, it is called stable sorting.

|Adaptive Sorting Algorithm	|Non-Adaptive Sorting Algorithm|
|---|---|
|A sorting algorithm is said to be adaptive, if it takes advantage of already 'sorted' elements in the list that is to be sorted. That is, while sorting if the source list has some element already sorted, adaptive algorithms will take this into account and will try not to re-order them.	|A non-adaptive algorithm is one which does not take into account the elements which are already sorted. They try to force every single element to be re-ordered to confirm their sortedness.|

- Increasing Order - 1, 3, 4, 6, 8, 9
- Non-Increasing Order - 1, 3, 3, 6, 8, 9
- Decreasing Order - 9, 8, 6, 4, 3, 1 
- Non-Decreasing Order - 9, 8, 6, 3, 3, 1

|Algorithm        |Best-case  |Worst-case |Average-case|Space Complexity   |Stable?|
|---              |---        |---        |---        |---                 |---|
|Bubble Sort      |Ο(n)       |Ο(n2)      |Ο(n2)      |Ο(1)                |Yes|
|Insertion Sort   |Ο(n)       |Ο(n2)      |Ο(n2)      |Ο(1)                |Yes|
|Selection Sort   |Ο(n2)      |Ο(n2)      |
|Merge Sort       |Ο(n logn)  |Ο(n logn)  |Ο(n logn)  |Ο(n)                |Yes|
|Quicksort        |Ο(n logn)  |Ο(n2)      |Ο(n logn)  |Log n(best), n (avg)|Usually not*
|Heapsort         |Ο(n logn)  |Ο(n logn)  |Ο(n logn)  |Ο(1)                |No|
|Counting Sort    |Ο(k + n)   |Ο(k + n)   |Ο(k + n)   |Ο(k + n)            |Yes|

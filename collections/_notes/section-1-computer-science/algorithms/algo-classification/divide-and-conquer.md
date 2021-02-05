---
layout: post
title: Divide and Conquer
permalink: /:collection/cs/algorithms/divide-and-conquer/intro
---

- TOC
{:toc}

<hr><br>

A problem using following three steps
- Divide: Break the given problem into subproblems of same type.
- Conquer: Recursively solve these subproblems.
- Combine: Appropriately combine the answers.

# Standard D&C Alogorithms
 
Binary Search is a searching algorithm. 
- In each step, the algorithm compares the input element x with the value of the middle element in array. 
	- values match, return the index of middle.
	- if x is less than the middle element, then the algorithm recurs for left side of middle element, 
	- else recurs for right side of middle element.

Quicksort is a sorting algorithm. 
- Picks a pivot element
- Rearranges the array elements with all smaller elements to left side of pivot, and all greater elements to right side. 
- Finally, the algorithm recursively sorts the subarrays on left and right of pivot element.

Merge Sort is also a sorting algorithm. 
- The algorithm divides the array in two halves, recursively sorts them and finally merges the two sorted halves.

Closest Pair of Points (To find the closest pair of points in a set of points in x-y plane)
- Normal Solution, O(n^2) time, by calculating distances of every pair of points and comparing to find the minimum. 
- The Divide and Conquer algorithm solve the problem in O(n Logn) time.

Strassen’s Algorithm (an efficient algorithm to multiply two matrices)
- Simple method to multiply two matrices need 3 nested loops and is O(n^3). 
- Strassen’s algorithm multiplies two matrices in O(n^2.8974) time.

Cooley–Tukey Fast Fourier Transform (FFT) algorithm is the most common algorithm for FFT. 
- It is a divide and conquer algorithm which works in O(n logn) time.

Karatsuba algorithm for fast multiplication 
- Multiplication of two n-digit numbers in at most 3n^(log2 3) = 3n^(1.585)                                                      
- single-digit multiplications in general (and exactly n^(log2 3) when n is a power of 2).                             
- It is therefore faster than the classical algorithm, which requires n2 single-digit products. If n = 2^10 = 1024, in particular, the exact counts are 3^10 = 59,049 and (2^10)^2 = 1,048,576, respectively.

Divide and Conquer (D & C) vs Dynamic Programming (DP)
- Both paradigms (D&C and DP) divide the given problem into subproblems and solve subproblems. 

How to choose one of them for a given problem? 
- D&C should be used when same subproblems are not evaluated many times. 
- Otherwise Dynamic Programming or Memorization should be used. 
- For example, Binary Search is a Divide and Conquer algorithm, we never evaluate the same subproblems again. On the other hand, for calculating nth Fibonacci number, Dynamic Programming should be preferred.
---
layout: post
title: Collections.sort algorithm
permalink: /:collection/java/collections/collections-sort-algorithm
---

**What sorting algorithm is used by Java's Collections.sort(), and why?**  
* Merge sort - fast, stable sorting, O(n log(n)). For Object References.
* Merge sort requires additional scratch space proportional to the size of the input array.
* Quicksort - primitive values, have no identity.
* Uses **Tim Sort** - stable, adaptive, iterative mergesort, O(n logn) time (worst case).
* Tim Sort is also called hybrid Sort, ***Insertion Sort + Modified Merge Sort***.
* Timsort uses insertion sort for very small amounts of data (more efficient for n < N, threshold).
* **Modified Mergesort** - used by java.util.Arrays.sort and (indirectly) by java.util.Collections.sort for object references.
* Here, merge is omitted if highest(low sublist) < lowest(high sublist)
 
java 7, Sort used **tim sort algorithm** which is mixture off merge sort and the binary search and it is also called the hybrid sort because it can sort all the datatype. Tim sort has o (n) running time in worst case but it comes under sequential sort algorithm in java.

Java 8, Sort used **parallel sort algorithm** on the basis of the granularity of the array or the size of array
* Best for data as large as 1 million
* Lower than granularity, sort by using dual pivot sort.
* Higher than granularity, sort by other type of sorting
* Java 8 sort algorithm work on the fork/join framework which used work stealing algorithm to sort.

```java
public static void parallelSort(double[] a) {
	int n = a.length, p, g;
    if (n <= MIN_ARRAY_SORT_GRAN || (p = ForkJoinPool.getCommonPoolParallelism()) == 1)
    	DualPivotQuicksort.sort(a, 0, n - 1, null, 0, 0);
    else
    	new ArraysParallelSortHelpers.FJDouble.Sorter(null, a, new double[n], 0, n, 0, ((g = n / (p << 2)) <= MIN_ARRAY_SORT_GRAN) ? MIN_ARRAY_SORT_GRAN : g).invoke();
}
```

* Minimum granularity, java.util.Arrays.MIN_ARRAY_SORT_GRAN = 8192 [0x2000])
* `Array length < minimum granularity`, sorted using the ***DualPivotQuicksort.sort*** directly instead of the sorting task partition. Typically, using smaller sizes results in memory contention across tasks that makes parallel speedups unlikely.

* `ForkJoinPool.getCommonPoolParallelism()` returns the targeted parallelism level of the common pool 
	- by default, equal to the number of available processors Runtime.getRuntime().availableProcessors().
	- If your machine has only 1 worker thread, it will not use parallel task either.

When the array length reaches a minimum granularity and you got more than 1 worker thread, the array is sorted using the parallel sort method. And the ForkJoin common pool is used to execute parallel tasks.

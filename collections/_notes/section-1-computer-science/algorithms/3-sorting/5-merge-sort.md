---
layout: post
title: Merge Sort
permalink: /:collection/cs/algorithms/sorting/merge-sort
---

- TOC
{:toc}

<hr><br>

# Merge Sort

- Divide and Conquer Algorithm.
- It divides input array in two halves, calls itself for the two halves and then merges the two sorted halves. The merge() function is used for merging two halves. 

Merge sort is a sorting technique based on divide and conquer technique. With worst-case time complexity being Ο(n log n), it is one of the most respected algorithms. 

Merge sort first divides the array into equal halves and then combines them in a sorted manner.

![merge-sort.png]({{site.cdn}}/cse/algo/sort/merge-sort.png)

# Algorithm

```
Step 1 − if it is only one element in the list it is already sorted, return.
Step 2 − divide the list recursively into two halves until it can no more be divided.
Step 3 − merge the smaller lists into new list in sorted order. 
```

# Pseudo Code

```java
procedure mergesort( var a as array )
   if ( n == 1 ) return a
   var l1 as array = a[0] ... a[n/2]
   var l2 as array = a[n/2+1] ... a[n]
   l1 = mergesort( l1 )
   l2 = mergesort( l2 )
   return merge( l1, l2 )
end procedure

procedure merge( var a as array, var b as array )
   var c as array
   while ( a and b have elements )
      if ( a[0] > b[0] )
         add b[0] to the end of c
         remove b[0] from b
      else
         add a[0] to the end of c
         remove a[0] from a
      end if
   end while   
   while ( a has elements )
      add a[0] to the end of c
      remove a[0] from a
   end while   
   while ( b has elements )
      add b[0] to the end of c
      remove b[0] from b
   end while   
   return c    
end procedure
```

# Merge Sort for Arrays
The merge(arr, l, m, r) is key process that assumes that arr[l..m] and arr[m+1..r] are sorted and merges the two sorted sub-arrays into one.
 
### STEPS: 
MergeSort(arr[], l,  r), If r > l
1. Find the middle point to divide the array into two halves:  middle m = (l+r)/2
2. Call mergeSort for first half: Call mergeSort(arr, l, m)
3. Call mergeSort for second half: Call mergeSort(arr, m+1, r)
4. Merge the two halves sorted in step 2 and 3: Call merge(arr, l, m, r)

- Time Complexity: T(n) = 2T(n/2) + O(n)
- O(nLogn) for all 3 cases (worst, average and best) as merge sort always divides the array in two halves and take linear time to merge two halves.
- Auxiliary Space: O(n)
- Sorting In Place: No in a typical implementation
- Stable: Yes

# Merge Sort for Linked Lists
 
Preferred for sorting a linked list as slow random-access performance of a linked list makes some other algorithms (such as quicksort) perform poorly, and others (such as heapsort) completely impossible.

![merge-sort-for-list.png]({{site.cdn}}/cse/algo/sort/merge-sort-for-list.png)

# Applications of Merge Sort
- [Inversion Count Problem](https://www.geeksforgeeks.org/counting-inversions/){:target="_blank"}
- Used in [External Sorting](https://en.wikipedia.org/wiki/External_sorting){:target="_blank"}
- [For sorting linked lists in O(nLogn) time](https://www.geeksforgeeks.org/merge-sort-for-linked-list/){:target="_blank"}


# Further
- 3-way Merge sort
- Merge sort for doubly linked list
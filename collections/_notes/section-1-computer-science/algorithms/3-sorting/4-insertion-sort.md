---
layout: post
title: Insertion Sort
permalink: /:collection/cs/algorithms/sorting/insertion-sort
---

![insertion-sort.png]({{site.cdn}}/cse/algo/sort/insertion-sort.png)

```
Time - O(n2)
Auxillary Sapce – O(1)   key
```

An in-place comparison-based sorting algorithm. Here, a sub-list is maintained which is always sorted. For example, the lower part of an array is maintained to be sorted. An element which is to be 'insert'ed in this sorted sub-list, has to find its appropriate place and then it has to be inserted there. Hence the name, insertion sort.

The array is searched sequentially and unsorted items are moved and inserted into the sorted sub-list (in the same array). This algorithm is not suitable for large data sets as its average and worst case complexity are of Ο(n2), where n is the number of items.

**Algorithm**
```
Step 1 − If it is the first element, it is already sorted. return 1;
Step 2 − Pick next element
Step 3 − Compare with all elements in the sorted sub-list
Step 4 − Shift all the elements in the sorted sub-list that is greater than the value to be sorted
Step 5 − Insert the value
Step 6 − Repeat until list is sorted
```

**Pseudo Code**
```java
procedure insertionSort( A : array of items )
   int holePosition
   int valueToInsert    
   for i = 1 to length(A) inclusive do:    
      /* select value to be inserted */
      valueToInsert = A[i]
      holePosition = i      
      /*locate hole position for the element to be inserted */        
      while holePosition > 0 and A[holePosition-1] > valueToInsert do:
         A[holePosition] = A[holePosition-1]
         holePosition = holePosition -1
      end while        
      /*insert the number at hole position*/
      A[holePosition] = valueToInsert      
   end for
end procedure
```

```java
for j = 2 to A.length{
  key = A[j];
  // insert A[j] into sorted sequence
  i = j-1;
  while (i>0 and A[i] > key){ A[i+1] = A[i]; i--; }
  A[i+1] = key;
}

Inner loop is dependent on outer, need to unroll
j = 2 to n ---> n-1
j= 2 i= 1 time
j=3 i=2time
j=n i=n-1 time
Total Executions = (n-1)(n)/2
```

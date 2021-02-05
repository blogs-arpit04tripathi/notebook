---
layout: post
title: Asymptotic Analysis
permalink: /:collection/cs/ds/algorithms-analysis/asymptotic
---

**Asymptotic Analysis**
- Evaluate performance of an algorithm in terms of input size (not actual running time). 
- Calculate how does the time (or space) taken by an algorithm increases with the input size.

**Does Asymptotic Analysis always work?**
- we always talk about input sizes larger than a constant value.
  - If such large input never given, we may end up choosing an algorithm that is Asymptotically faster but slower for our specific requirement.
- Algorithms 1000nLogn, 2nLogn asymptotically same (order of growth is nLogn). can’t judge as we ignore constants.

**Space Complexity**
- **Auxiliary Space**, extra space or temporary space used by an algorithm.
- **Space Complexity**, (Auxiliary space + space used by input) = (total space taken with respect to input size)
- Example, compare standard sort algorithms based of space, Auxiliary Space is better criterion than Space Complexity.
  - Merge Sort - O(n) auxiliary space
  - Insertion sort - O(1) auxiliary space
  - Heap Sort use - O(1) auxiliary space
  - but all have Space complexity O(n).

**Worst Case Analysis (Usually Done)**
- Calculate upper bound, case that causes maximum number of operations to be executed.
- Linear Search, when the element to be searched is not present in the array. O(n).

**Average Case Analysis (Sometimes done)**
- All possible inputs and calculate computing time for all of the inputs. 
- Sum all calculated values and divide by total number of inputs. We must know (or predict) distribution of cases. 
- Linear Search, assume all cases are uniformly distributed (also x not present).

**Best Case Analysis (Bogus)**
- Calculate lower bound, case that causes minimum number of operations to be executed. 
- Linear Search, when x is present at the first location. Θ(1).

||||
|---|---|---|
|**Merge Sort**|Cases|all the cases are asymptotically same, i.e., there are no worst and best cases.<br>Merge Sort does Θ(n logn) operations in all cases.|
|**Insertion sort**|Worst|when the array is reverse sorted|
|   |Best|when the array is sorted in the same order as output.|
|**Quick Sort**|Worst|when the input array is already sorted. (where pivot is chosen as a corner element)|
|   |Best|when the pivot elements always divide array in two halves.|
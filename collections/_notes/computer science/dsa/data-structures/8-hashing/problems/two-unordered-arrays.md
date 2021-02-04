---
layout: post
title: Check 2 Unordered Arrays
permalink: /:collection/cs/ds/hashing/two-unordered-arrays
---

```
A = {2,5,6,8,10,2,2}
B = {2,5,5,8,10,5,6}
```

# Solution 1
- For each element in A, check element is in B or not.
- Problem - Duplicates (number of occurences)

# Solution 2 (Sorting)
- Sort and iterate over both to check the elements
- Time - O(n logn) ~ O(n logn) + O(n)

# Solution 3 (Hashing)
- Create frequency map for A.
- For each element in B, decrease frequency.
- Map should be empty.
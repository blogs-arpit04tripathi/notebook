---
layout: post
title: Arrays Left Rotation
permalink: /:collection/cs/ds/arrays/left-rotation
---


**Write a function rotate(ar[], d, n) that rotates arr[] of size n by d elements.**

### Method 1 (Using temp array)
Input arr[] = [1, 2, 3, 4, 5, 6, 7], d = 2, n =7
1) Store d elements in a temp array: temp[] = [1, 2]
2) Shift rest of the arr[]: arr[] = [3, 4, 5, 6, 7, 6, 7]
3) Store back the d elements:    arr[] = [3, 4, 5, 6, 7, 1, 2]

- Time complexity : O(n)
- Auxiliary Space : O(d)

### Method 2 (Rotate one by one)
```
leftRotate(arr[], d, n)
start
  For i = 0 to i < d
    Left rotate all elements of arr[] by one
end
```
- Time complexity : O(n * d)
- Auxiliary Space : O(1)

### Method 3 (A Juggling Algorithm)
This is an extension of method 2. Instead of moving one by one, divide the array in different sets where number of sets is equal to GCD of n and d and move the elements within sets.

n =12 and d = 3. GCD is 3. 

Let arr[] be {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12}
1. Elements are first moved in first set
    - arr[] after this step --> {`4` 2 3 `7` 5 6 `10` 8 9 `1` 11 12}
2. Then in second set.
    - arr[] after this step --> {4 `5` 3 7 `8` 6 10 `11` 9 1 `2` 12}
3. Finally in third set.
    - arr[] after this step --> {4 5 `6` 7 8 `9` 10 11 `12` 1 2 `3`}

![rotate-left-juggle.png]({{site.cdn}}/cse/ds/array/rotate-left-juggle.png)
- Time complexity: O(n)
- Auxiliary Space: O(1)

My thoughts- Make block of size d rather than GCD of n,d

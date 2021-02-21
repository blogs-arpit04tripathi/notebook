---
layout: post
title: Arrays in Java
permalink: /:collection/java/arrays
---

- **Array** : common name for homogeneous collection accessible by index.
- ***length*** - array capacity to hold elements, not element count.

```java
// month_days is an array variable, no array actually exists
int month_days[];
// Links with an actual, physical array of integers. Memory allocated.
month_days = new int[12];
// array initializer
int month_days[] = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};
```

# Multidimensional arrays 
* arrays of arrays. 
* new statement - ***leftmost dimension required mandatorily***.
* default value for new    : 
	- zero (for numeric types)
	- false (for boolean)
	- null (for reference types)

```java
int twoD[][] = new int[4][];        // leftmost dimension required
System.out.println(twoD.length);    // prints 4
System.out.println(twoD[0]);        // prints null
twoD[0] = new int[5];
twoD[1] = new int[5];
twoD[2] = new int[5];
twoD[3] = new int[5];
```

![2d-array]({{site.cdn}}/java/core-java/2d-array.png)

# Irregular array – sparsely populated 2D array

```java
char twod1[][] = new char[3][4];
char[][] twod2 = new char[3][4];
```

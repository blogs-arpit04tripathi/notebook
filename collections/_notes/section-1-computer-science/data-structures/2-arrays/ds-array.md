---
layout: post
title: Arrays
permalink: /:collection/cs/ds/arrays/
---

- TOC
{:toc}

---

# Arrays

- One variable for homogeneous collection.
- Stored in Contiguous memory locations.
- Allow random access.
- have better [cache locality](https://en.wikipedia.org/wiki/Locality_of_reference), improving performance.
- Good for static size list otherwise double it and copy(overhead).

DS to store homogeneous elements at contiguous locations. Size to be provided before storing data.
- Accessing Time: O(1) [This is possible because elements are stored at contiguous locations]   
- Search Time   : O(n) for Sequential Search: O(log n) for Binary Search [If Array is sorted]
- Insertion Time: O(n) [worst case, insertion at Beginning and shifting all of the elements]
- Deletion Time : O(n) [worst case, deletion at Beginning and shifting all of the elements]

|Operations|||
|---|---|---|
|Access|O(1)||
|Insert|O(n)|Worst case - array is full, create new array and copy the old array elements.|
|Delete|O(n)|Worst case - deletion at index 0, all elements to be adjusted.|

- Arrays in C gave only warning but no **ArrayOutOfBoundException**.
- Java arrays are dynamically allocated at runtime “on the fly”.
- arrays have a member variable **public final field length** which is int and provided at construction time.
- direct superclass of an array type is [Object](https://www.geeksforgeeks.org/object-class-in-java/).
- Every array type implements the interfaces [Cloneable](https://www.geeksforgeeks.org/marker-interface-java/) and [java.io.Serializable](https://www.geeksforgeeks.org/serialization-in-java/).
- *Storage specification*
  - A **local array** will be (usually) created on **stack**.
  - A **global or static array** will be (usually) created on **bss/data segments**
  - A **dynamically created array** will be created on **heap**.
- For primitive data types, the actual values are stored in contiguous memory locations. 
- For objects, the actual objects are stored in heap segment.
- Can be Row Major (normally used) or Column Major. I prefer row major, for i -> j.
- **Capacity** - Max elements that can be stored in array, .length property of array.
  - `ArrayIndexOutOfBoundsException` for invalid index.
- **Length** - Current number of stored element, you must do a loop and check or keep a track yourself with some variable.
- For Coding Interview, it can be assumed that input arrays passed in methods are completely filled and .length will give capacity (upper bound index).

**Practical Uses of Array**
- Dynamic Programming
- Creating Hash Tables

## 1-D Array

![array.png]({{site.cdn}}/cse/ds/array/array.png)

## MultiDimensional Array

```java
int intArray[];         //declaring array
intArray = new int[20]; // allocating memory to array
// Default values
boolean : false, int : 0, double : 0.0, String : null, User Defined Type : null
//a 2D array or matrix
int[][] intArray = new int[10][20];                       
//a 3D array
int[][][] intArray = new int[10][20][10];
```
![array-2d.png]({{site.cdn}}/cse/ds/array/array-2d.png)
```java
int arr[][] = { {2,7,9},{3,6,1},{7,4,2} };
int arr[][] = new int[2][];
arr[0] = new int[3];
arr[1] = new int[2];
```
```java
for (int i=0; i<arr.length; i++) 
  for(int j=0; j<arr[i].length; j++) 
    arr[i][j] = count++;
```

### Jagged array
array of arrays such that member arrays can be of different sizes, i.e., we can create a 2-D arrays but with variable number of columns in each row.

![array-jaggered]({{site.cdn}}/cse/ds/array/array-jaggered.png)

# Cloning of arrays
- 1D array, “deep copy” is performed.
- 2D array, “shallow copy” creates only a single new array with each element array a reference to an original element array but subarrays are shared.

![array-clone.png]({{site.cdn}}/cse/ds/array/array-clone.png)

# Arrays as Dynamic List

- no adequate max size
- on array becoming full, insertion needs creation of new array and copy old items.
  - contiguous memory of required size may not be available.

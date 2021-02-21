---
layout: post
title: Arrays class
permalink: /:collection/java/collections/arrays-class
---


* **Arrays** class - provides methods to bridge the gap between collections and arrays.

**List from Array**  
```java
static <T> List asList(T... array) // List backed by array, both the list and the array refer to the same location
static void fill(char array[ ], char value)
static void setAll(double array[ ])
static void parallelSetAll(double array[ ])
```

**Algo - Binary Search**  
```java
static int binarySearch(char array[ ], char value)
static <T> int binarySearch(T[ ] array, T value, Comparator<? super T> c)
```

**CopyOf**  
```java
static char[ ] copyOf(char[ ] source, int len)
static <T,U> T[ ] copyOf(U[ ] source, int len, Class<? extends T[ ]> resultT)
```

**CopyOfRange**  
```java
static char[ ] copyOfRange(char[ ] source, int start, int end)
static <T,U> T[ ] copyOfRange(U[ ] source, int start, int end,  Class<? extends T[ ]> resultT)
```

**equals**  
```java
static boolean equals(char array1[ ], char array2 [ ])
static boolean deepEquals(Object[ ] a, Object[ ] b)     // nested arrays
```

**Algo - Sort**  
```java
static void sort(int array[ ])
static <T> void sort(T array[ ], Comparator<? super T> c)
static void parallelSort(int array[ ])
static <T> void parallelSort(T array[ ], Comparator<? super T> c)
```

**Stream**  
```java
static DoubleStream stream(double array[ ])
static IntStream stream(int array[ ])
static LongStream stream(long array[ ])
static <T> Stream stream(T array[ ])
```

**Split Iterator**  
```java
static Spliterator.OfDouble spliterator(double array[ ])
static Spliterator.OfInt spliterator(int array[ ])
static Spliterator.OfLong spliterator(long array[ ])
static <T> Spliterator spliterator(T array[ ])
```

**Util Methods**  
```java
toString()
deepToString()
hashCode()
deepHashCode()
IntToDoubleFunction<? extends T> genVal)
IntToDoubleFunction<? extends T> genVal)
static void parallelPrefix(double array[ ], DoubleBinaryOperator func)
```

# copyOf( )
* longer than source, default padding **0, null ,false**.
* In the last form, the type of resultT becomes the type of the array returned. 
	- If len is negative, a **NegativeArraySizeException** is thrown. 
	- If source is null, a **NullPointerException** is thrown. 
	- If resultT is incompatible with the type of source, an **ArrayStoreException** is thrown.

# copyOfRange( )
* If start is negative or greater than the length of source, an **ArrayIndexOutOfBoundsException** is thrown. 
* If start is greater than end, an **IllegalArgumentException** is thrown. 
* If source is **null**, a **NullPointerException** is thrown. 
* If resultT is incompatible with the type of source, an **ArrayStoreException** is thrown.

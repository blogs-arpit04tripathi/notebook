---
layout: post
title: Collections class
permalink: /:collection/java/collections/collections-class
---

* **Collections** class - several algorithms as static methdos.
* **checked methods** - returns “dynamically typesafe view” of a collection, Compatibility check at run time (insertion).
  * Example **checkedCollection(), checkedSet( ), checkedList( ), checkedMap( )**, and so on.
* synchronized (thread-safe) copies - **synchronizedList(), synchronizedSet()**.
* General rule, standard collections implementations are not synchronized. 
* One other point: ***iterators to synchronized collections must be used within synchronized blocks***.

**Add/Insert**  
```java
static <T> Boolean addAll(Collection<? super T> c, T... elements)
static <T> boolean replaceAll(List<T> list, T old, T new)
static <T> void fill(List<? super T> list, T obj) 
```

**Algo - Min/Max/Frequency**  
```java
static <T> T max(Collection<? extends T> c, Comparator<? super T> comp)
static <T extends Object & Comparable<? super T>> T max(Collection<? extends T> c)
static <T> T min(Collection<? extends T> c, Comparator<? super T> comp)
static <T extends Object & Comparable<? super T>> T min(Collection<? extends T> c)
static int frequency(Collection<?> c, object obj) 
```

**Algo - Binary Search**  
```java
static <T> int binarySearch(List<? extends Comparable<? super T>> list, T value)
static <T> int binarySearch(List<? extends T> list, T value, Comparator<? super T> c)
```

**Algo - Sort/Reverse**  
```java
static <T> void sort(List<T> list, Comparator<? super T> comp)
static <T extends Comparable<? super T>> void sort(List<T> list)
static void reverse(List<T> list) 
static <T> Comparator<T> reverseOrder(Comparator<T> comp)       // returns reversal comparator
static <T> Comparator<T> reverseOrder( )
```

**Checked Collection**  
```java
static <E> Collection<E> checkedCollection(Collection<E> c, Class<E> t)
static <E> List<E> checkedList(List<E> c, Class<E> t)
static <E> Queue<E> checkedQueue(Queue<E> q, Class<E> t)
static <E> List<E> checkedSet(Set<E> c, Class<E> t)
static <E> NavigableSet<E> checkedNavigableSet(NavigableSet<E> ns, Class<E> t)
static <E> SortedSet<E> checkedSortedSet(SortedSet<E> c, Class<E> t)
static <K, V> Map<K, V> checkedMap(Map<K, V> c, Class<K> keyT, Class<V> valueT)
static <K, V> NavigableMap<K, V> checkedNavigableMap(NavigableMap<K, V> nm, Class<E> keyT, Class<V> valueT)
static <K, V> SortedMap<K, V> checkedSortedMap(SortedMap<K, V> c, Class<K> keyT, Class<V> valueT)
```

**Copy**  
```java
static <T> void copy(List<? super T> list1, List<? extends T> list2)  // Copies the elements of list2 to list1.
```

**Empty Collections**  
```java
static <T> List<T> emptyList( ) 
static <T> Set<T> emptySet( ) 
static <E> NavigableSet<E> emptyNavigableSet( )
static <E> SortedSet<E> emptySortedSet( ) 
static <K, V> Map<K, V> emptyMap( ) 
static <K, V> NavigableMap<K, V> emptyNavigableMap( )
static <K, V> SortedMap<K, V> emptySortedMap( )
```

**Iterate/Enumerate**  
```java
static <T> Iterator<T> emptyIterator( )
static <T> ListIterator<T> emptyListIterator( )
static <T> Enumeration<T> emptyEnumeration( )
static <T> Enumeration<T> enumeration(Collection<T> c)
```

**SubList**  
```java
static int indexOfSubList(List<?> list, List<?> subList)
static int lastIndexOfSubList(List<?> list, List<?> subList)
static <T> ArrayList<T> list(Enumeration<T> enum)
```

**Misc**  
```java
static <T> Queue<T> asLifoQueue(Deque<T> c) 
static <E> Set<E> newSetFromMap(Map<E, Boolean> m)
static boolean disjoint(Collection<?> a, Collection<?> b)   // true, when no common elements 
static <T> List<T> nCopies(int num, T obj)                  // Returns num copies of obj in immutable list. num >=0.
```

**Operations – Rotate/Shuffle/Swap**  
```java
static void rotate(List<T> list, int n)             // Rotates list by n places to the right. -ve to left rotate.
static void shuffle(List<T> list, Random r) 
static void shuffle(List<T> list) 
static void swap(List<?> list, int idx1, int idx2) // Exchanges the elements in list at the indices specified by idx1 and idx2.
```

**Singleton**  
```java
static <T> Set<T> singleton(T obj) 
static <T> List<T> singletonList(T obj) 
static <K, V> Map<K, V> singletonMap(K k, V v)
```

**Synchronized**  
```java
static <T> Collection<T> synchronizedCollection(Collection<T> c)
static <T> List<T> synchronizedList(List<T> li) 
static <T> Set<T> synchronizedSet(Set<T> s) 
static <T> NavigableSet<T> synchronizedNavigableSet(NavigableSet<T> ns)
static <T> SortedSet<T> synchronizedSortedSet(SortedSet<T> ss)
static <K, V> Map<K, V> synchronizedMap(Map<K, V> m)
static <K, V> NavigableMap<K, V> synchronizedNavigableMap(NavigableMap<K, V> nm)
static <K, V> SortedMap<K, V> synchronizedSortedMap(SortedMap<K, V> sm)
```

**Unmodifiable**  
```java
static <T> Collection<T> unmodifiableCollection(Collection<? extends T> c)
static <T> List<T> unmodifiableList(List<? extends T> list)
static <T> Set<T> unmodifiableSet(Set<? extends T> s)
static <T> NavigableSet<T> unmodifiableNavigableSet(NavigableSet<T> ns)
static <T> SortedSet<T> unmodifiableSortedSet(SortedSet<T> ss)
static <K, V> Map<K, V> unmodifiableMap(Map<? extends K, ? extends V> m)
static <K, V> NavigableMap<K, V> unmodifiableNavigableMap(NavigableMap<K, ? extends V> nm)
static <K, V> SortedMap<K, V> unmodifiableSortedMap(SortedMap<K, ? extends V> sm)
```

**Collections** defines three static variables: **EMPTY_SET**, **EMPTY_LIST**, and **EMPTY_MAP**. All are immutable.

|FAQ||
|---|---|
|How to get read-only Collections?                  |`Collections.unmodifiableCollection(Collection c)`, throw UnsupportedOperationException|
|How to reverse the List in Collections?            |`Collections.reverse(listobject)`          |
|How to convert the array of strings into the list? |`Arrays.asList(wordArray)`                 |
|How can we sort a list of Objects?                 | `Arrays.sort()` or `Collections.sort()`   |

* overloaded sort() methods - natural sorting (Comparable) and custom sorting (Comparator).
* ***Collections.sort internally uses Arrays.sort sorting method, so they have same performance except that Collections take sometime to convert list to array***.

**Why java.util.Arrays uses Two Sorting Algorithms?**  

> Read article [here](http://cafe.elharo.com/programming/java-programming/why-java-util-arrays-uses-two-sorting-algorithms/){:target="_blank"}

|		|		|   |
|---|---|---|
|**Quick sort (dual pivot quicksort)**	|primitive types such as int								                |worst case - O(n^2)|
|**Merge sort**							            |for objects that implement Comparable or use a Comparator.	|worst case - O(n log n)|

* Mergesort is stable in both cases. 
* Quicksort is faster in both cases. For primitive, Quicksort is stable too.

```java
[7, 6, 6, 7, 6, 5, 4, 6, 0] // All 6 are same as they don’t hold object references. 
```
* If using objects, maybe space is not a critical and extra space used by a merge sort maybe not be a problem.
* If using primitive, maybe performance is most important so they use quick sort.

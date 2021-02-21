---
layout: post
title: Generic Interfaces
permalink: /:collection/java/generics/interfaces
---

- TOC
{:toc}

<hr><br>

* Generic interfaces are specified just like generic classes.

```java
interface MinMax<T extends Comparable<T>> {
    T min();    T max();
}
class MyClass<T extends Comparable<T>> implements MinMax<T> {   // No need to define upper bound twice
    T[] vals;
    MyClass(T[] o) {
        vals = o;
    }
    public T min() {        // return type T
        T min = vals[0];
        for (int i = 1; i<vals.length; i++)
            if (vals[i].compareTo(min) < 0)
                min = vals[i];
        return min;
    }
}
```

* Once type parameter defined, it is passed to interface without modification.

```java
class MyClass<T extends Comparable<T>> implements MinMax<T> {
class MyClass<T extends Comparable<T>> implements MinMax<T extends Comparable<T>> {// wrong!
```
* ***If class implements generic interface, then class must also be generic. It should takes a type parameter to pass to interface.***

```java
class MyClass implements MinMax<T> {            // Wrong!   MyClass doesn’t have a type parameter, cannot pass any to interface
class MyClass implements MinMax<Integer> {      // OK       but of no use as it’s no more generic
```

* **Generic interface offers two benefits:**
	- First, it can be implemented for different types of data.
	- Second, it allows you to put constraints (that is, bounds) on the types of data.


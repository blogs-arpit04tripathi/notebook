---
layout: post
title: Using Wildcard Arguments
permalink: /:collection/java/generics/wildcards
---

- TOC
{:toc}

<hr><br>

# Using Wildcard Arguments
* example, **Stats** class has a method **sameAvg()** to find if two **Stats** have arrays with same average, any numeric type.
boolean sameAvg(Stats<?> ob)

```java
boolean sameAvg(Stats<T> ob) {      // This won't work!
  if(average() == ob.average())     // this object (type T), ob is also type T. Will not work for int/long/double combination
    return true;
  return false;
}
// Not feasible with current method definition as both iob and dob needs to be of same types
System.out.println("iob sameAvg(dob) - " + iob.sameAvg(dob));
```
* Problem with code here, work only with other **Stats** of same type as the invoking object.
* To make a generic **sameAvg()** method, use the *wildcard argument*, **?**, representing unknown type.
* **wildcard does not affect what type of Stats objects can be created; this is governed by the extends clause.**

```java
boolean sameAvg(Stats<? extends Number> ob) {
    if(average() == ob.average())     // Will work for int/long/double combination
        return true;
    return false;
}
```

# Bounded Wildcards
* Wildcard arguments can be bounded.
* upper bound - **extends** (<? extends superclass>) 
* lower bound - **super**  (<? super subclass>)
* call to **showXZY( )** on **Coords<TwoD>** reference will give compile-time error, thus ensuring type safety.

```java
class TwoD {  int x, y; }
class ThreeD extends TwoD {   int z;  }
class FourD extends ThreeD {  int t;  }
class Coords<T extends TwoD> {	
      T[] coords;
      Coords(T[] o) { coords = o; }
}
static void showXY(Coords<?> c) {...}                     // Valid for all 2D,3D,4D
static void showXYZ(Coords<? extends ThreeD> c) {...}     // Valid for 3D,4D
```

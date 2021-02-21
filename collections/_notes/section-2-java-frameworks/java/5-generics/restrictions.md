---
layout: post
title: Generics Restrictions
permalink: /:collection/java/generics/restrictions
---

- TOC
{:toc}

<hr><br>

# Type Parameters Can’t Be Instantiated
- T is a placeholder, not well-defined type.

```java
class Gen<T> {
    T ob;
    Gen() { ob = new T(); }     // Illegal!!!
}
```

# Restrictions on Static Members
- No static member can use a type parameter declared by the enclosing class, static are class level but T is at instance level.

```java
class Wrong<T> {
   static T ob;                     // Wrong, no static variables of type T.
   static T getob() { return ob; }  // Wrong, no static method can use T.
   // generic static method with its own type param is OK
   static <T extends Comparable<T>, V extends T> boolean isIn(T x, V[] y){...}
}
```

# Generic Array Restriction
* cannot instantiate an array of type parameter. 
* cannot create an array of type-specific generic references.

```java
class Gen<T extends Number> {
    T ob;
    T[] vals;
    Gen(T o, T[] nums) {
        ob = o;
        vals = nums;
        // vals = new T[10];   // can't create an array of T
    }
}

public static void main(String args[]) {
    Integer n[] = { 1, 2, 3, 4, 5 };
    Gen<Integer> iOb = new Gen<Integer>(50, n);
    // Gen<Integer> gens[] = new Gen<Integer>[10];  // Wrong!
    // Gen<Long> gensLong[] = new Gen<Long>[10];  // Wrong!
    // gens[0] = gensLong[0];  // Wrong! this is why generic array of type is not allowed
    Gen<?> gens[] = new Gen<?>[10];                 // OK
}
```
* No direct type casting of arrays on type-erasure.  `(int[]) Object[]`
* You can create an array of references to a generic type if you use a wildcard.

# Generic Exception Restriction
* A generic class ***cannot extend Throwable***.
* you ***cannot create generic exception classes***.
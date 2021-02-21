---
layout: post
title: Raw Types and Legacy Code
permalink: /:collection/java/generics/raw-types
---

- TOC
{:toc}

<hr><br>

* Pre-generics code must be compatible with generics. 
* **For transition to generics, Java allows a generic class to be used without any type arguments.**
* This creates a **raw type** for the class compatible with legacy code, having no knowledge of generics. 
* The main drawback to using the **raw type** is that the **type safety of generics is lost**.
* Due to potential errors, **javac gives *unchecked warnings* on use of raw type** as it might jeopardize type safety.

```java
class Gen<T> {
    T ob;
    Gen(T o) { ob = o; }
    T getob() { return ob; }
}

class RawDemo {
    public static void main(String args[]) {
        Gen<Integer> iOb = new Gen<Integer>(88);
        Gen<String> strOb = new Gen<String>("Generics Test");
        Gen raw = new Gen(new Double(98.6));
        double d = (Double) raw.getob(); // Cast here is necessary because type is unknown.
        // int i = (Integer) raw.getob();     // run-time error
        strOb = raw; // OK, but potentially wrong
        // String str = strOb.getob();        // run-time error
        raw = iOb; // OK, but potentially wrong
        // d = (Double) raw.getob();          // run-time error
    }
}
```
* No type arguments, this creates a **Gen** object whose type **T** is replaced by **Object**.

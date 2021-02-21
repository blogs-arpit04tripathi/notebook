---
layout: post
title: Generic Methods
permalink: /:collection/java/generics/methods
---

- TOC
{:toc}

<hr><br>

* can have generic method that uses one or more type parameters of its own.
* **can create a generic method enclosed within a non-generic class, type parameters are declared before the return type.**
* **Generic methods can be either static or non-static.**

```java
class GenMethDemo { // Non-Generic Class with Generic method
    // Determine if an object is in an array.
    static <T extends Comparable<T> , V extends T> boolean isIn(T x, V[] y) {
        for (int i = 0; i < y.length; i++)
            if (x.equals(y[i]))
                return true;
        return false;
    }

    public static void main(String args[]) {
        Integer nums[] = { 1, 2, 3, 4, 5 };
        if (isIn(2, nums))
            System.out.println("2 is in nums");
        String strs[] = { "one", "two", "three" };
        if (isIn("two", strs))
            System.out.println("two is in strs");
        // if(isIn("two", nums))                    // Oops! Won't compile! Types must be compatible.
    }
}
```
* **types of the arguments** are automatically discerned, but **can also be explicitly specified**.

```java
GenMethDemo.<Integer, Integer>isIn(2, nums)
```

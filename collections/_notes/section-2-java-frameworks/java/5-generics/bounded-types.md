---
layout: post
title: Bounded Types
permalink: /:collection/java/generics/bounded-types
---

- TOC
{:toc}

<hr><br>


# Bounded Types

```java
class Stats<T extends Number> {     // Number or its subclass
    T[] nums;                       // array of Number or subclass
    Stats(T[] o) { nums = o; }
    double average() {              // Return type double in all cases.
        double sum = 0.0;
        for (int i = 0; i < nums.length; i++)
            sum += nums[i].doubleValue();
        return sum / nums.length;
    }
}
```

* limit or bound types that can be passed to type parameter. 
* For example, to calculate average of an array of numbers, any type of number (***integers, float, double***).
* ***\<T extends superclass> sets upper limit***

```java
Double dnums[] = { 1.1, 2.2, 3.3, 4.4, 5.5 };
Stats<Double> dob = new Stats<Double>(dnums);
System.out.println("dob average() - " + dob.average());
Integer inums[] = { 1, 2, 3, 4, 5 };
Stats<Integer> iob = new Stats<Integer>(inums);
System.out.println("iob average() - " + iob.average());
```

# Multiple Bounds

```java
<T extends superClassName & Interface>
```
```java
class Bound<T extends A & B> { 
  private T objRef; 
  public Bound(T obj){ this.objRef = obj; }    
  public void doRunTest(){ this.objRef.displayClass(); } 
}

public class BoundedClass { 
  public static void main(String a[]) { 
    Bound<A> bea = new Bound<A>(new A()); 
    bea.doRunTest();
  } 
}
```

* Multiple Bounds allowed.
  * A and B – both interface
  * A is class then B, C should be interfaces.

```java
interface B {
    public void displayClass();
}
class A implements B {
    public void displayClass() {
        sysout("Inside super class A");
    }
}
```

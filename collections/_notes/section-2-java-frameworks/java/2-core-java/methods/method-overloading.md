---
layout: post
title: Method Overloading
permalink: /:collection/java/method-overloading
---

* Method overloading = **compile-time polymorphism**
* ***type and number of arguments*** used to identify the version in use. 
* ***may have different return types.***
* In C, abs( ) - integer, labs( ) - long, fabs( ) - floating-point value.
* Sometimes, **automatic type conversions can help in overload resolution.**

```java
class OverloadDemo {
    void test() {}
    void test(int a, int b) {}
    void test(double a) {}
    
    public static void main(String args[]) {
        OverloadDemo ob = new OverloadDemo();
        int i = 88;
        ob.test(i);     // this will invoke test(double)
    }
}
```
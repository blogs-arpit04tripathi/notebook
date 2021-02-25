---
layout: post
title: this Keyword in Lambda Expression
permalink: /:collection/java/java8/this-keyword-in-lambda
---

- In Anonymous inner class, `this` refers to the instance of anonymous inner class even inside the static void main method.

```java
public class MyClass {
    public void doProcess(int i, Process p) {
        p.process(i);
    }

    public static void main(String[] str) {
        MyClass m = new MyClass();
        m.doProcess(10, new Process() {
            @Override
            public void process(int i) {
                System.out.println(i);
                System.out.println(this); // prints instance value of anonymous inner class
            }

            @Override
            public String toString() {
                "Inside Anonymous Inner Class";
            }
        });
    }
}
```
For Lambda, `this` is not overriden as opposed to the case of Anonymous Inner Class.
```java
public class MyClass {
    public void doProcess(int i, Process p) {
        p.process(i);
    }

    public static void main(String[] str) {
        MyClass m = new MyClass();
        m.doProcess(10, (i) - > {
            System.out.println(i);
            System.out.println(this); // compilation error
        });
    }
}
```

---
layout: post
title: Generic Constructors
permalink: /:collection/java/generics/constructors
---

- TOC
{:toc}

<hr><br>

* It is possible to **have generic constructors, even if their class is not**.

```java
class GenCons {
    private double val;
    <T extends Number> GenCons(T arg) {
        val = arg.doubleValue();
    }
    void showval() {
        System.out.println("val: " + val);
    }
}
class GenConsDemo {
    public static void main(String args[]) {
        GenCons test1 = new GenCons(100)        test1.showval(); // 100.0
        GenCons test2 = new GenCons(123.5F);    test2.showval();
    }
}
```

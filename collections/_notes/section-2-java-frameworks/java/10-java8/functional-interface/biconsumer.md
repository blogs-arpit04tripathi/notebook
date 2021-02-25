---
layout: post
title: Bi-Consumer
permalink: /:collection/java/java8/functional-interface/biconsumer
---


```java
// BiConsumer to compare 2 lists of integers 
BiConsumer < List < Integer > , List < Integer >> equals = (list1, list2) - > {
    if (list1.size() != list2.size()) {
        System.out.println("False");
    } else {
        for (int i = 0; i < list1.size(); i++)
            if (list1.get(i) != list2.get(i)) {
                System.out.println("False");
                return;
            }
        System.out.println("True");
    }
};
```
```java
// BiConsumer to print 2 lists 
BiConsumer < List < Integer > , List < Integer > > disp = (list1, list2) - > {
    list1.stream().forEach(a - > System.out.print(a + " "));
    System.out.println();
    list2.stream().forEach(a - > System.out.print(a + " "));
    System.out.println();
};

// Using addThen() method 
equals.andThen(disp).accept(lista, listb);
```

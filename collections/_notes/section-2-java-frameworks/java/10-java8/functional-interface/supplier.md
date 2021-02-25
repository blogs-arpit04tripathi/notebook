---
layout: post
title: Supplier
permalink: /:collection/java/java8/functional-interface/supplier
---


* Similar to factory method or new() which return an object.
* get() - no argument and return an object.
* **Primitive**: IntSupplier getAsInt(), LongSupplier getAsLong(), DoubleSupplier getAsDouble(), BooleanSupplier getAsBoolean()

```java
public interface Supplier {  T get();  } 
Supplier < Person > supplier = () - > { return new Person("Varun", 30, "Programmer");  };
Person p = supplier.get();
names.stream().forEach( (item) ->  {  printNames( () -> item ); }  )
private static void main printNames(Supplier<String> supplier){  System.out.println(supplier.get());  }
```

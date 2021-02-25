---
layout: post
title: Consumer
permalink: /:collection/java/java8/functional-interface/consumer
---


* Represents an operation that accepts a single input argument and returns no result.
* abstract method accept(T t) and default method andThen(Consumer<? super T> after)
* Primitive: 
	- IntConsumer accept(int), 
	- DoubleConsumer accept(double), 
  - LongConsumer accept(long)

```java
Consumer<String> consumer = ConsumerTest::pritName;
Consumer.accept(“Java”);
Consumer.accept(“Java8”);
pritName(String name){  System.out.println(name); }
```

```java
@FunctionalInterface
public interface Consumer<T> {
  void accept(T t);
  default Consumer < T > andThen(Consumer << ? super T > after) {
        Objects.requireNonNull(after);
        return (T t) - > { accept(t);    after.accept(t);  };
  }
}

Consumer < String > consumer1 = arg -> {System.out.println(arg + "OK");};
consumer1.accept("TestConsumerAccept - ");
Consumer < String > consumer2 = (x) - > { System.out.println(x + "OK!!!");};
consumer1.andThen(consumer2).accept("TestConsumerAfterThen - ");
```

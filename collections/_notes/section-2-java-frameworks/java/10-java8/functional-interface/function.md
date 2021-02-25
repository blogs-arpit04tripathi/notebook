---
layout: post
title: Function
permalink: /:collection/java/java8/functional-interface/function
---

* Function<T, R> in java.util.function. 
* for mapping scenarios i.e when an object of a type is taken as input and it is converted(or mapped) to another type. 
* Common usage - streams .map() converts type of stream.

```java
@FunctionalInterface
public interface Function < T, R > {
    R apply(T t);
    default < V > Function < V, R > compose(Function << ? super V, ? extends T > before) {
        Objects.requireNonNull(before);
        return (V v) - > apply(before.apply(v));
    }
    default < V > Function < T, V > andThen(Function << ? super R, ? extends V > after) {
        Objects.requireNonNull(after);
        return (T t) - > after.apply(apply(t));
    }
    static < T > Function < T, T > identity() {
        return t - > t;
    }
}
```

---
layout: post
title: Predicate
permalink: /:collection/java/java8/functional-interface/predicate
---


* boolean-valued function of one argument, used with stream filter.
* method - test()
* java.util.function

|Methods	          | Description |
|---                |---          |
|boolean test(T t)	| evaluates predicate on given argument.|
|default Predicate<T> and(Predicate<? super T> other)	| AND (short-circuit)|
|default Predicate<T> negate()	| predicate which is logical negation of this predicate.|
|default Predicate<T> or(Predicate<? super T> other)	|OR (short-circuit)|
|static <T> Predicate<T> isEqual(Object targetRef)	|tests if two arguments are equal, Objects.equals(Object, Object).|

```java
public class PredicateInterfaceExample {
    public static void main(String[] args) {
        Predicate < Integer > pr = a - > (a > 18);
        System.out.println(pr.test(10));
    }
}

public class PredicateInterfaceExample {
    static Boolean checkAge(int age) {
        return (age > 17 ? true : false);
    }
    public static void main(String[] args) {
        Predicate < Integer > predicate = PredicateInterfaceExample::checkAge;
        System.out.println(predicate.test(25));
    }
}
```

**What is the difference between Predicate and Function?**  
* Predicate - single argument function, returns either true or false.
* Function<T,R>   (T input, R result) - single argument function, returns an object. 
* Both can be used as an assignment target for lambda expressions or method references.

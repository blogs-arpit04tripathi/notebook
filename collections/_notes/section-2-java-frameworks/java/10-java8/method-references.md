---
layout: post
title: Method References
permalink: /:collection/java/java8/method-references
---

* Used for referencing a method without invoking it ie. for treating methods as Lambda Expressions. 
* They only work as syntactic sugar to reduce the verbosity of some lambdas.
* a double colon separating a class or object name and the name of the method. 

```java
(o) -> o.toString(); // === Object::toString();
p -> System.out.println(p); // === System.out::println

// Method Reference can be used in below example case
() -> method()
p -> method(p)
```

|Method References                  |                   |
|---                                |---                |
|constructor reference              | String::new;      |
|Static method reference            | String::valueOf;  |
|Bound instance method reference    | str::toString;    |
|Unbound instance method reference	| String::toString; |

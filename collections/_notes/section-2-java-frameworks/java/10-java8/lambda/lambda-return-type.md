---
layout: post
title: Return Type of Lambda
permalink: /:collection/java/java8/lambda-return-type
---

The type of a lambda expression depends on the context it is being used.
- Return type of Lambda Function is Fucntional Interface.
- Lambda is used to implement the functional interfaces as well.
- When method argument is a Functional interface, lambda expression automatically detects and implements the functional interface as anonymous function given number of arguments matched for lambda and functional interface.

```java
MyLambda myLambdaFunction = () -> System.out.println("Hello World!");
// interface
interface MyLambda{
    void foo();
}
```
```java
// Here you create a impl class
MyLambda myLambda = new MyLambdaImpl();
// Here only function is created
MyLambda myLambdaFunction = () -> System.out.println("Hello World!");
// kind of Anonymous interface
// its somewhat similar to Anonymous inner class, except reduced memory footprint in jar
MyLambda innerMyLambda = new MyLambda(){
    public void perform(){
        System.out.println("Hello World!");
    }
};
```

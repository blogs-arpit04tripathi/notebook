---
layout: post
title: Exception Handling in Lambda
permalink: /:collection/java/java8/exception-handling-in-lambda
---


**Can lambda expression throw exception? Is there any restriction in lambda expression exception handling?**  
lambda expression can throw exception compatible with the throws clause of functional interface method.

```java
public static void main(String[] args){
  int[] numbers = {1,2,3,4,5,6};
  int key = 0;
  process(numbers, key, (v,k)-> System.out.println(v/k));
  // we can put try catch around the lambda expression
  // but it will not be concise and readable anymore, hence not recommended
}

private static void process(int[] numbers, int key, BiConsumer<Integer, Interger> biConsumer){
  for(int i: numbers)
    biConsumer.accept(i, key);
    // here biConsumer is divide operation causing ArithmeticException
    // but biConsumer can be any operation making list of catch very long
    // hence not recommended to do exception handling here
}
```
Recommended way is to wrap the lambda and handle the exception there.
```java
// passing wrapperLambda rather than original lambda
process(numbers, key, wrapperLambda((v,k)-> System.out.println(v/k)));

private static Biconsumer<Integer, Integer> wrapperLambda(Biconsumer<Integer, Integer> biConsumer){
  return (v,k) -> {
    try{
      biConsumer.accept(v,k);
    } catch(ArithmeticException e){
      e.printStackTrace();
    }
  }
}
```

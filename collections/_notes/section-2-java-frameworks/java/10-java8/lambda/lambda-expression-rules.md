---
layout: post
title: Lambda Expression Rules
permalink: /:collection/java/java8/lambda-expression-rules
---

- parentheses are compulsory, when zero or more than two arguments. 
- curly braces are compulsory, when lambda expressions has more than 1 line. 
- Usually, do not have more line of code in lambda expression due to readability. (call function from expression body)
- ***return statement is optional in lambda***.
    - ***That means (a, b) – > {return a+b;} and (a, b) – > {a+b;} are both valid.***
- lambda expression must have same parameter type as the parameter in the function of the interface.
- It must also return a type compatible with the return type of function.

```java
(a,b)->System.out.println(a,b);
a -> return a*2;
()->System.out.println(“Method Called”);

a->{   a = a*2+5;   System.out.println(a);  }
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
numbers.forEach(t -> System.out.println(t));
```

**(int x, y) -> x + y; is this a valid lambda expression?**  
No

**(int x, int y) -> x+y; or (x, y) -> x + y; which one of these is a valid lambda expression?**  
Both of them are valid lambda expressions if used in a correct context.
* (int x, int y) -> x+y;     parameters must be of type int.
* (x, y) -> x + y;         in correct context, type can be inferred for the lambda expression.

**What is block lambda expression?**  

```java
(num) -> {  int fact = 1; return fact; } // Block or multiline Lambda.
(String s1, String s2) -> s1+s2;         // single expression lambda.
```

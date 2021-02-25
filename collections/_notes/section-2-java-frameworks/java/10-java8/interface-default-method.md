---
layout: post
title: Interface Default Method
permalink: /:collection/java/java8/interface-default-method
---


- Interface default method - to add new functionalities without breaking the existing implementation of the interface.
- Usually, for a new interface method, all classes need to implement it. This problem has been solved by the use of default method.
- Example, forEach() in Collection interface. default implementation provided for all classes of collection.

```java
public interface MyInterface {
    public void existingMethod();
    default public void newDefaultMethod() {
        System.out.println("New default method added.");
    }
}
```

**Is it possible to implement two interfaces having default method with same name and signature? Explain with example.**  
Here the compiler gives an error saying that “Duplicate Default Methods”. Hence it is not possible to implement two interfaces with the same name and signature.
```java
public class HelloJava8 implements Interface1, Interface2 {
  public static void main(String[] args){
    DefaultMethodInterface defMethIn = new HelloJava8();
    defMethIn.defaultMethod();
  }
}
```

**What is the purpose of a Static method in an Interface in Java 8?**  
A Static method in an Interface is utility or helper method. 
* **Single Class**: no need to create a separate Utils class for utility or helper methods.
* **Encapsulation**: With Static methods, complete behavior of a Class is encapsulated in same class.
* **Extension**: It is easier to extend a Class/API. example extend ArrayList, we get all the methods. No need to extend Collections class also.

**How does Java 8 solve Diamond problem of Multiple Inheritance?**  
* When a class extends 2 or more classes with different implementations of same method then it causes Diamond problem.
* **ChildClass** gives compile time error, compiler cannot decide which display method should it invoke in ChildClass.

```java
public interface BaseInterface{    default void display() { /*code*/} }
public interface BaseOne extends BaseInterface { }
public interface BaseTwo extends BaseInterface { }
public class ChildClass implements BaseOne, BaseTwo { }
// Solution
BaseOne.super.display(); solves the Diamond problem as it resolves the confusion for compiler.

public interface A{     default void display() { /*code*/} }
public interface B extends A{ }
public interface C extends A{ }
public class D implements B,C{
  default void display() { B.super.display(); }
}
```

**Can we have default method in an interface without marking it with default keyword?**  
No, compile time error.

**Can a class implement two Interfaces with default methods of same name and signature?**  
No, Diamond Problem.

**What are the main differences between an interface with default method and an abstract class in Java 8?**

||Interface	| Abstract Class|
---|---|---
Instance variable	| No            | Yes
Constructor	        | No            | Yes
Concrete Method     | Only default  | Yes
Lambda	            | Functional Interface can be used with lambda  | Cannot be used with Lamda

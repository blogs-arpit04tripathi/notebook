---
layout: post
title: final Keyword
permalink: /:collection/java/final
---

* final in java are by **default read-only**.
* class, method, and variables. 
* static final constant.
* **Cannot change reference after assigning (compile error)**.
* final member variable must be **initialized on declaration or via constructor**.
* Only final variable is accessible inside anonymous class in Java. (Anonymous Inner Class without a name)
* **interface variables are implicitly final**.

# final variables in Java

```java
public static final String LOAN = "loan";
LOAN = new String("loan")                   //invalid compilation error
```

* final reference variable of collection means **only reference can not be changed but you can update** the same collection.

```java
private final List loans = new ArrayList();
loans.add("home loan");                     //valid
loans.add("personal loan");                 //valid
loans = new Vector();                       //not valid
```

# final method in Java
* can not be overridden.
* when method is complete and its behavior should remain constant in sub-classes. 
* final methods are faster than non-final methods because they are not required to be resolved during run-time.
* final methods are bonded **during compile time** also called **static binding**.

```java
class PersonalLoan{
    public final String getName(){return "personal loan";}
}
```
```java
class CheapPersonalLoan extends PersonalLoan{
    @Override
    public final String getName(){ return "cheap personal loan";}
    //compilation error: overridden method is final
}     
```

* Inlining is an option only with final methods. 
* Normally, **methods calls are dynamically resolved at run time**, called **late binding**. 
* As final methods cannot be overridden, method call can be **resolved at compile time**, called **early binding**.
* Here, Compiler is free to inline calls to final methods as they cannot be overridden by a subclass.
* When a small final method is called, often the **Java compiler can copy the bytecode for the subroutine directly inline with the compiled code of the calling method**, thus eliminating the costly overhead associated with a method call.

# final Class in Java
* **cannot be inherited**.
* example: **String, Integer and other wrapper classes**.
* **methods of final class are implicitly final**. 

```java
final class PersonalLoan {}
class CheapPersonalLoan extends PersonalLoan {
    //compilation error: cannot inherit from final class
}
```

# Benefits of final keyword 
* final keyword improves performance.
* JVM and application can cache final variable.
* **Safe to share in [multi-threading](https://javarevisited.blogspot.com/2011/02/how-to-implement-thread-in-java.html) environment without additional synchronization overhead**.

# final and Immutable Class in Java
* can not be modified once created. Example – **String**. 
* required to **make a class immutable** in java.
* Immutable classes are read-only and safely shared in between multiple threads without any synchronization overhead. 
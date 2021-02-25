---
layout: post
title: Functional Interface
permalink: /:collection/java/java8/functional-interface
---

* Frequently used classes **Runnable**, **Comparator**, **Callable** etc have only one method declared to be implemented, called Single Abstract Method (SAM). 
* It is normally implemented using anonymous class.

#### Functional Interface
* can have exactly one abstract method.
* any number of default or static methods.
* Can even override Object class method.
* public Object methods are considered implicit members of functional interface as they are automatically implemented by an instance of functional interface.
* If interface extends a Functional interface without adding any new abstract method, then it is also a Functional interface.

**Can we have a generic functional interface?**  
No
* Lambda expression doesn't have type parameters of its own so it can't be generic. 
* But functional interface specifying the target type of lambda expression can be generic.

```java
@FunctionalInterface
interface GenInterface<T, U, R> {R addValues(T t, U u);}
```

**Is it mandatory to mark @FunctionalInterface?**  
* Not mandatory to mark @FunctionalInterface annotation.
* Exclusively annotated, Java Compiler forces to use one and only one abstract method for that interface.

**Why do we need Functional Interfaces?**  
Type of Lambda Expression is a Functional Interface. Using lambda expressions means using Functional Interfaces.

**Is it possible to define our own Functional Interface? Explain the rules to define a functional interface.**  

```java
@FunctionalInterface
public interface MyComparator {
  public boolean compareMyValues(int a, int b);
}

MyComparator mycomp = (a,b) -> a>b;
System.out.println("Is 4 > 5: "+ mycomp.compareMyValues(4, 5));
```

**Will the below code compiles without error?**

```java
@FunctionalInterface
public interface Function2<T, U, V> {
  public V apply(T t, U u);
  default void count() {
    // increment counter
  }
}
```
Yes
* only a single abstract method.
* Other method is default method.

**Describe some of the functional interfaces in the standard library.**  
package - java.util.functionConsumer – it takes one argument and returns no result (represents a side effect)
* Predicate – it takes one argument and returns a boolean 
* Function – it takes one argument and returns a result
* BiFunction – it takes two arguments and returns a result
* Supplier – it takes not argument and returns a result
* Consumer - 
* BiConsumer - 
* UnaryOperator – it is similar to a Function, taking a single argument and returning a result of the same type
* BinaryOperator –similar to BiFunction, two arguments and result are all of the same types

**What is the difference between a normal and functional interface in Java?**  

|Normal Interface	| Functional Interface|
---|---
|Any number of abstract methods|Exactly 1
||wrap function as an interface, function is represented by the single abstract method|

**Comparator is functional interface but has a lot of other methods, how is it a Single Abstract method interface?**  
* Allowed interface to have default methods and static methods.
* Only one abstract method.
* Override Object class public methods too, as they are consider implicit methods.

**How can we write comparator as lambda expression?**

```java
// Option 1
Collections.sort(personList, new Comparator<Person>() {
   public int compare(Person a, Person b) {
     return a.getFirstName().compareTo(b.getFirstName());
   }
});

// Option 2
Collections.sort(personList, (Person a, Person b) -> a.getFirstName().compareTo(b.getFirstName()));

// Option 3
Comparator<Person> multiComparator = Comparator.comparing(Person::getFirstName);
multiComparator = multiComparator.thenComparing(Comparator.comparing(Person::getLastName));
Collections.sort(persons, multiComparator);
```

**How can we write runnable as lambda expression?**

```java
// Before Lambda
Thread th = new Thread(new Runnable() {
    @Override
    public void run() {
        System.out.println("Run thread");
    }
});
```
```java
// Using Lambda
Runnable r = () - > System.out.println("Run new thd");
Thread th = new Thread(r);
th.start();
```
**How can we write callable as lambda expression?**

```java
ExecutorService es = Executors.newFixedThreadPool(2);
getLength(es, "executor");
public static void getLength(ExecutorService es, final String str){
 // callable implemented as lambda expression
 Callable<String> callableObj = () -> {
   StringBuffer sb = new StringBuffer();
   return (sb.append("Length of string ").append(str).append(" is ")
	.append(str.length())).toString();
 };
 Future<String> f = es.submit(callableObj);
 try {  System.out.println("" + f.get());}
 catch (InterruptedException | ExecutionException e) {e.printStackTrace();}
}
```
**What are the differences between Predicate, Supplier and Consumer in Java 8?**  
* ***Predicate*** - accepts one argument and returns a boolean.
* ***Supplier***  - accepts no argument and returns a result.
* ***Consumer***  - accepts one argument and returns no result.

---
layout: post
title: Type Annotations – JDK8
permalink: /:collection/java/annotations/type-annotations
---


* With JDK 8, annotations can be used in new places which were originally allowed only on declarations.
* can annotate return type of method, type of **this** in a method, a cast, array levels, an inherited class, and a **throws** clause.
* can also annotate generic types, including generic type parameter bounds and generic type arguments.
* type annotation must include **ElementType.TYPE_USE** as a target.
* For example, assuming some type annotation called **@TypeAnno**, the following is legal:

```java
void myMeth() throws @TypeAnno NullPointerException { // ...
```
* You can also annotate the type of **this** (called the *receiver*).
	- this is an implicit argument to all instance methods and it refers to the invoking object. 
	- To annotate its type requires a new JDK 8 feature where you can explicitly declare this as 1st param to a method.
	- In this declaration, the type of this must be the type of its class.
```java
int myMeth(@TypeAnno SomeClass this, int i, int j) { // …
```
  - It is not necessary to declare **this** unless you are annotating it. 
	- If **this** is not declared, it is still implicitly passed. JDK 8 does not change **this** fact.
	- Also, explicitly declaring **this** does not change the method’s signature because **this** is implicitly declared, by default.

![annotations-type]({{site.cdn}}/java/reflection/annotations-type.png)

* **@EmptyOK, @Recommended, @What** - not type annotations, included for comparison purposes.
* **@What** - used to annotate a generic type parameter declaration.

```java
// Demonstrate several type annotations.
import java.lang.annotation.*;
import java.lang.reflect.*;
// Marker Annottions
@Target(ElementType.TYPE_USE)
@interface TypeAnno { }
@Target(ElementType.TYPE_USE)
@interface NotZeroLen {}
@Target(ElementType.TYPE_USE)
@interface Unique { }
@Target(ElementType.TYPE_USE)
@interface MaxLen {int value();}
@Target(ElementType.TYPE_PARAMETER)
@interface What {String description();}
@Target(ElementType.FIELD)
@interface EmptyOK { }
@Target(ElementType.METHOD)
@interface Recommended { }

class TypeAnnoDemo<@What(description = "Generic data type") T> {                // type parameter.
  public @Unique TypeAnnoDemo() {}                                              // type on a constructor
  @TypeAnno String str;                                                         // Annotate the type (here, String), not the field.
  @EmptyOK String test;                                                         // Annotates field.
  public int f(@TypeAnno TypeAnnoDemo<T> this, int x) {  return 10;  }          // Annotate this
  public @TypeAnno Integer f2(int j, int k) {  return j+k;}                     // Annotate the return type
  public @Recommended Integer f3(String str) {return str.length() / 2;}         // Annotate method declaration
  public void f4() throws @TypeAnno NullPointerException {...}                  // Type annotation on throws clause
  String @MaxLen(10) [] @NotZeroLen [] w;                                       // Annotate array levels
  @TypeAnno Integer[] vec;                                                      // Annotate array element
  public static void myMeth(int i) {
    TypeAnnoDemo<@TypeAnno Integer> ob = new TypeAnnoDemo<@TypeAnno Integer>(); //Annotate type argument
    @Unique TypeAnnoDemo<Integer> ob2 = new @Unique TypeAnnoDemo<Integer>();    // type annotation with new.
    Object x = new Integer(10);
    Integer y;
    y = (@TypeAnno Integer) x;                                                  // type annotation on a cast.
  }
  public static void main(String args[]) {  myMeth(10);  }
  class SomeClass extends @TypeAnno TypeAnnoDemo<Boolean> {}                    // type annotation with inheritance clause.
}
```

---
layout: post
title: Java Annotations
permalink: /:collection/java/annotations/
---

# Annotations

* To embed supplemental information into a source file, it does not change the actions of a program. 
* An annotation is created through a mechanism based on the **interface**.
* consist solely of method declarations with no bodies as java provides implementation.
* methods act much like fields.

```java
@interface MyAnno {
  String str() default "Testing";
  int val() default 100;
}
```
* An annotation cannot include an **extends** clause as they automatically extend the **Annotation** interface. 
* package - **java.lang.annotation**.
* overrides **hashCode( ), equals( )**, and **toString( )** defined by **Object**.
* **annotationType()** - returns a **Class** object that represents the invoking annotation.
* *classes, methods, fields, parameters, **enum** constants and even annotation can be annotated.*
* the annotation precedes the rest of the declaration.

```java
@MyAnno(str = "Annotation Example", val = 100)
public static void myMeth() { // …
```
* When an annotation member is given a value, only its name is used. Thus, annotation members look like fields in this context.

# Specifying a Retention Policy

* Retention policy - determines when an annotation is discarded. 
* **java.lang.annotation.RetentionPolicy** enum - **SOURCE, CLASS**, and **RUNTIME**.
    - SOURCE – annotation is retained only in the source file and is discarded during compilation.
    - CLASS – retained till **.class** during compilation, discarded by JVM during run time.
    - RUNTIME - available for JVM runtime also. greatest annotation persistence.
* An annotation on a local variable declaration is not retained in the .class file.

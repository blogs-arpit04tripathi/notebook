---
layout: post
title: Repeating Annotations
permalink: /:collection/java/annotations/repeating-annotations
---


* JDK 8 annotation - enables annotation to be repeated on the same element, must be annotated with the **@Repeatable**.
* **value** field specifies the container type for the repeatable annotation, an array of the repeatable annotation type.

```java
// Make MyAnno repeatable.
@Retention(RetentionPolicy.RUNTIME)
@Repeatable(MyRepeatedAnnos.class)
@interface MyAnno {String str() default "Testing"; int val() default 9000;}
// This is the container annotation.
@Retention(RetentionPolicy.RUNTIME)
@interface MyRepeatedAnnos { MyAnno[] value(); }
```
* In **getAnnotation()**, use the container annotation, not the repeatable annotation.

```java
The output is shown here:
@MyRepeatedAnnos(value=[@MyAnno(str=First annotation, val=-1),
@MyAnno(str=Second annotation, val=100)])
```
repeated annotations are separated by a comma. They are not returned individually.
* **getAnnotationsByType()** and **getDeclaredAnnotationsByType()**.

```java
Annotation[] annos = m.getAnnotationsByType(MyAnno.class);
for(Annotation a : annos){ System.out.println(a); }
```

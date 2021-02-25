---
layout: post
title: AnnotatedElement Interface
permalink: /:collection/java/annotations/annotated-element-interface
---

# java.lang.reflect.AnnotatedElement`
* `getAnnotation()`
* `getAnnotations()`
* Annotation[ ] `getDeclaredAnnotations()` - all non-inherited annotations
* `isAnnotationPresent(Class<? extends Annotation> annoType)`

* JDK 8 adds `getDeclaredAnnotation()`, `getDeclaredAnnotationsByType()`, and `getAnnotationsByType()`. 
* Last two automatically work with a repeated annotation.

# Marker Annotations
* contains no members, used to mark an item. And check it using `isAnnotationPresent()`.
* @MyMarker() and @MyMarker both are valid.
* @MyMarker is used without parenthesis due to no members present.

# Single-Member Annotations
* Only one member or all other with default values.
* Allows shorthand representation - @MySingle(100)

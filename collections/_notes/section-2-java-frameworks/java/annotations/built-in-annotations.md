---
layout: post
title: Built-in Annotations
permalink: /:collection/java/annotations/built-in-annotations
---

# java.lang.annotation
* ***used with other annotations only***.
* **@Retention** - used only as an annotation to another annotation to specify retention policy.
* **@Documented** - marker annotation that tells a tool that an annotation is to be documented. 
* **@Inherited** - marker annotation. Makes the annotation inheritable to a subclass.
* **@Target** - types of items allowed for annotation and takes one argument, array of constants of the ElementType enumeration.
* If you don't use @Target, all are allowed except type parameters.

![annotations-target.png]({{site.cdn}}/java/reflection/annotations-target.png)

```java
@Target( { ElementType.FIELD, ElementType.LOCAL_VARIABLE } )
```

# java.lang
* **@Override** - marker annotation for methods. ensure methods are overridden not simply overloaded, compile-time error caused.
* **@Deprecated** - marker annotation that a declaration is obsolete and has been replaced by a newer form.
* **@FunctionalInterface** - marker annotation(JDK 8) for interfaces. Indicates an interface with only one abstract method. 
    - Functional interfaces are used by lambda expressions.
    - It is purely informational, not mandatory. It becomes only by definition of exactly one abstract method.
* **@SafeVarargs** - marker annotation for methods and constructors. 
	- It indicates that no unsafe actions related to a varargs parameter occur and suppress unchecked warnings.
	- It must be applied only to vararg methods or constructors that are static or final.
* **@SuppressWarnings**
    - specifies warnings that might be issued by the compiler are to be suppressed. The warnings to suppress are specified by name, in string form.

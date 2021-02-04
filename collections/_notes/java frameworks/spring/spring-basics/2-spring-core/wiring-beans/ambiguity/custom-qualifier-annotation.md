---
layout: post
title: Annotation @Qualifier
permalink: /:collection/spring/annotation/custom-qualifier
---

```java
@Component
@Qualifier("cold")
public class Popsicle implements Dessert { ... }
```

- Java doesn’t allow multiple annotations of the same type to be repeated on the same item.
- Here, you can create custom qualifier annotations to represent the traits you want your beans to be qualified with. 
- All you have to do is create an annotation that is itself annotated with @Qualifier. Rather than use @Qualifier("cold"), you can use a custom @Cold annotation that’s defined like this:

```java
@Target({ElementType.CONSTRUCTOR, ElementType.FIELD, ElementType.METHOD, ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Qualifier
public @interface Cold { }
```
```java
@Component
@Cold 
public class IceCream implements Dessert { ... }
```

**NOTE** : Java 8 allows repeated annotations, as long as the annotation is annotated with @Repeatable. Even so, Spring’s @Qualifier annotation isn’t annotated with @Repeatable.

- With custom qualifier annotations, you can use multiple qualifiers together without any complaints from the Java compiler.
- Your custom annotations are more type-safe than raw @Qualifier annotation with qualifier as a String.

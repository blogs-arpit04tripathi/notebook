---
layout: post
title: Annotation @Basic
permalink: /:collection/hibernate/annotations/basic
---

By default, properties and instance variables in your POJO are persistent; Hibernate will store their values for you. The simplest mappings are therefore for the "basic" types. These include primitives, primitive wrappers, arrays of primitives or wrappers, enumerations, and any types that implement Serializable but are not themselves mapped entities.

These are all mapped implicitly—no annotation is needed. By default, such fields are mapped to a single column, and eager fetching is used to retrieve them. Also, when the field or property is not a primitive, it can be stored and retrieved as a null value. This default behavior can be overridden by applying the @Basic annotation to the appropriate class member

```java
@Basic (fetch = FetchType.LAZY, optional = false)	// false means associated column should be created NOT NULL
private String  firstName;
```

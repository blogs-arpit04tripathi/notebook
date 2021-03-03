---
layout: post
title: Annotation @Transient
permalink: /:collection/hibernate/annotations/transient
---

Some fields, such as calculated values, may be used at run time only, and they should be discarded from objects as they are persisted into the database. The JPA specification provides the @Transient annotation for these transient fields. 
```java
@Transient
private Integer age;
```
Static or transient – doesn’t save to DB

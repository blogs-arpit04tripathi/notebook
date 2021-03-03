---
layout: post
title: Annotation @Entity
permalink: /:collection/hibernate/annotations/entity
---

It marks this class as an entity bean, so it **must have a no-argument constructor** that is visible.

```java
@Entity
public class EmployeeEntity implements Serializable{
    public EmployeeEntity(){    }
    //Other code
}
```

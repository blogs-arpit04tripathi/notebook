---
layout: post
title: JPA 2 Annotations
permalink: /:collection/hibernate/annotations
---

**Annotation**

- ***Needs access of source code to modify mapping.***

```java
import javax.persistence.* ;
@Entity
public class Sample {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    public Integer id;
    public String name;
}
```

**Mapping**

- ***Useful when source code is not available***

```xml
<?xml version='1.0' encoding='utf-8'?>
<!DOCTYPE hibernate-mapping 
  PUBLIC
   "-//Hibernate/Hibernate Mapping DTD//EN"
   "http://hibernate.sourceforge.net/hibernate-mapping-3.0.dtd">
<hibernate-mapping default-access="field">
   <class name="Sample">
      <id type="int" column="id">
         <generator class="native"/>
      </id>
      <property name="name" type="string"/>
   </class>
</hibernate-mapping>
```


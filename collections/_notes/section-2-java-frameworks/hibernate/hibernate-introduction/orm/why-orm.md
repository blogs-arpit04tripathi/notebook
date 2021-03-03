---
layout: post
title: Why ORM?
permalink: /:collection/hibernate/orm/why
---

![orm]({{site.cdn}}/hibernate/orm.png)

**'Object-Relational Impedance Mismatch'** (sometimes called the 'Paradigm Mismatch') is just a fancy way of saying that object models and relational models do not work very well together.

Other ORM - Enterprise JavaBeans Entity Beans, Java Data Objects, Castor, TopLink, Spring DAO, Hibernate etc.

Consider below objects need to be stored and retrieved into the following RDBMS table:
-	1st problem, what if we need to modify the design of our database after having developed few pages or our application?
-	2nd problem, Loading and storing objects in a relational database exposes us to the following five mismatch problems.

```java
public class Employee {
   private int id;
   private String first_name; 
   private String last_name;   
   private int salary; 
   public Employee() {}
   // getter-setters
}
```
```sql
create table EMPLOYEE (
   id INT NOT NULL auto_increment,
   first_name VARCHAR(20) default NULL,
   last_name  VARCHAR(20) default NULL,
   salary     INT  default NULL,
   PRIMARY KEY (id)
);
```

RDBMS represent data in a tabular format, whereas object-oriented languages, such as Java, represent it as an interconnected graph of objects. Loading and storing graphs of objects using a tabular relational database exposes us to **5 mismatch problems**.

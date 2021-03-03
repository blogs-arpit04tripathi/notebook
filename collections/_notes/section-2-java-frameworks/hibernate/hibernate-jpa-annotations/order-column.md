---
layout: post
title: Annotation @OrderColumn
permalink: /:collection/hibernate/annotations/order-column
---

```java
@OneToMany
@OrderColumn( name="employeeNumber" )
List<Employee> employees;
```
-	Here, we are declaring that an employeeNumber column will maintain a value, starting at 0 and incrementing as each entry is added to the list. The default starting value can be overridden by the base attribute. 
-	By default, the column can contain null (unordered) values. The nullability can be overridden by setting the nullable attribute to false. 
-	By default, when the schema is generated from the annotations, the column is assumed to be an integer type; however, this can be overridden by supplying a columnDefinition attribute specifying a different column definition string.


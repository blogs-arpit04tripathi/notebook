---
layout: post
title: Annotation @Table and @SecondaryTable
permalink: /:collection/hibernate/annotations/table
---

By default, table names are derived from the entity names. Therefore, given a class Employee with a simple @Entity annotation, the table name would be "employee", adjusted for the database’s configuration. If the entity name is changed (by providing a different name in the @Entity annotation, such as **@Entity("EMP_MASTER"))**, the new name will be used for the table name.

**@Table** annotation provides four attributes, allowing you to override the name of the table, its catalog, and its schema, and to enforce unique constraints on columns in the table. 

**@SecondaryTable** annotation provides a way to model an entity bean that is persisted across several different database tables.

your entity bean can have an @SecondaryTableannotation, or an @SecondaryTables annotation in turn containing zero or more @SecondaryTable annotations. 

`@SecondaryTable` annotation takes the same basic attributes as the @Table annotation, with the addition of the join attribute. The join attribute defines the join column for the primary database table. It accepts an array of javax.persistence.PrimaryKeyJoinColumn objects. If you omit the join attribute, then it will be assumed that the tables are joined on identically named primary key columns.

```java
@Entity
@Table(name = "employee")
@SecondaryTable(name = "employee_details")
public class EmployeeEntity implements Serializable {
   @Id
   @GeneratedValue (strategy = GenerationType.SEQUENCE)
   private Integer employeeId;
   private String  firstName;
   private String  lastName;
 
   @Column(table = "employee_details")
   public String address;
}
```
```java
@Entity
@Table(
  name="employee",
  uniqueConstraints={@UniqueConstraint(columnNames="firstName")}
  )
@SecondaryTable(name = "employee_details")
public class EmployeeEntity implements Serializable{}
```

Columns in the primary or secondary tables can be marked as having unique values within their tables by adding one or more appropriate @UniqueConstraint annotations to @Table or @SecondaryTable’s uniqueConstraints attribute. Alternatively, You may also set uniqueness at the field level with the unique attribute on the @Column attribute.


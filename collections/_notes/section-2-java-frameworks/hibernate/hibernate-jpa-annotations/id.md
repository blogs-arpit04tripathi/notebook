---
layout: post
title: Primary Keys with @Id and @GeneratedValue
permalink: /:collection/hibernate/annotations/id
---

- **Natural Key** – email ID for business logic, Needs to provided with a value
- **Surrogate Key** – Primary Key (No business significance), serial number column. Hibernate can generate.

```java
@Id
private Integer employeeId;
```
```java
@Id
public Integer getEmployeeId(){   return employeeId;  }
```

Property access means that Hibernate will call the mutator/setter instead of actually setting the field directly, what it does in case of field access. This gives flexibility to alter the value of actual value set in id field if needed. Additionally, you can apply extra logic on setting of ‘id’ field in mutator for other fields as well.

```java
@Id
@GeneratedValue (strategy = GenerationType.SEQUENCE)
private Integer employeeId;
 
//OR a more complex use can be
 
@Id
@GeneratedValue(strategy=GenerationType.TABLE ,generator="employee_generator")
@TableGenerator(name="employee_generator",
  table="pk_table",
  pkColumnName="name",
  valueColumnName="value",
  allocationSize=100)
private Integer employeeId;
```

the default GenerationType is AUTO.

There are four different types of primary key generators on GeneratorType, as follows:
1.	**AUTO**: Hibernate decides which generator type to use, based on the database’s support for primary key generation.
2.	**IDENTITY**: The database is responsible for determining and assigning the next primary key.
3.	**SEQUENCE**: Some databases support a SEQUENCE column type. It uses @SequenceGenerator.
4.	**TABLE**: This type keeps a separate table with the primary key values. It uses @TableGenerator.

The generator attribute allows the use of a custom generation mechanism shown in above code example.

```java
@Id
@GeneratedValue(strategy=SEQUENCE,generator="seq1")
@SequenceGenerator(name="seq1",sequenceName="HIB_SEQ")
private Integer employeeId;
```
Use strategy as IDENTITY for some some DB, SEQUENCE for some other DB.

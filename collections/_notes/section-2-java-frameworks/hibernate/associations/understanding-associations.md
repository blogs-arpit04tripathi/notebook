---
layout: post
title: Understanding Associations with Example
permalink: /:collection/hibernate/associations
---

Two simple entities (AccountEntity and EmployeeEntity) for this example and then create one-to-one association. 

```java
@Entity
@Table(name = "Account")
public class AccountEntity implements Serializable{
   private static final long serialVersionUID = 1L;
 
   @Id
   @Column(name = "ID", unique = true, nullable = false)
   @GeneratedValue(strategy = GenerationType.SEQUENCE)
   private Integer accountId;
 
   @Column(name = "ACC_NO", unique = false, nullable = false, length = 100)
   private String accountNumber;
 
   //We will define the association here
   EmployeeEntity employee;
 
   //Getters and Setters are not shown for brevity
}
```

```java
@Entity
@Table(name = "Employee")
public class EmployeeEntity implements Serializable{
   private static final long serialVersionUID = -1798070786993154676L;
   @Id
   @Column(name = "ID", unique = true, nullable = false)
   @GeneratedValue(strategy = GenerationType.SEQUENCE)
   private Integer employeeId;
   @Column(name = "FIRST_NAME", unique = false, nullable = false, length = 100)
   private String firstName;
   @Column(name = "LAST_NAME", unique = false, nullable = false, length = 100)
   private String lastName;
 
   //We will define the association here
   AccountEntity account; 
   //Getters and Setters are not shown for brevity
}
```

---
layout: post
title: One to One Mapping Annotation
permalink: /:collection/hibernate/mapping/one-to-one
---

Various supported techniques for one to one mapping
1. Using foreign key association
2. Using common join table
3. Using shared primary key

In hibernate there are 3 ways to create one-to-one relationships between two entities. Either way we have to use @OneToOneannotation.
1.	First technique is most widely used and uses a **foreign key column in one of the tables.**
2.	Second technique uses a rather known solution of having a **third table to store mapping** between first two tables.
3.	Third technique is something new which uses a **common primary key value in both the tables.**

# 1. Foreign Key

![]({{site.cdn}}/hibernate/121-foreign-key.png)

```java
EmployeeEntity.java
@OneToOne
@JoinColumn(name="ACCOUNT_ID")
private AccountEntity account;

AccountEntity.java
@OneToOne(mappedBy="account")
private EmployeeEntity employee;
```

-	@JoinColumn annotation which looks like the @Column annotation. It has one more parameters named referencedColumnName. This parameter declares the column in the targeted entity that will be used to the join.
-	If no @JoinColumn is declared on the owner side, the defaults apply. A join column(s) will be created in the owner table and its name will be the concatenation of the name of the relationship in the owner side, _ (underscore), and the name of the primary key column(s) in the owned side.

In a bidirectional relationship, one of the sides (and only one) has to be the owner. The owner is responsible for the association column(s) update. To declare a side as not responsible for the relationship, the attribute mappedBy is used. ‘mappedBy’ refers to the property name of the association on the owner side.

```
Console
Hibernate: insert into ACCOUNT (ACC_NUMBER) values (?)
Hibernate: insert into Employee (ACCOUNT_ID, EMAIL, FIRST_NAME, LAST_NAME) values (?, ?, ?, ?)
```

# 2. with common join table

![]({{site.cdn}}/hibernate/121-join-table.png)

main annotation to be used is @JoinTable. This annotation is used to define the new table name (mandatory) and foreign keys from both of the tables.

```java
@OneToOne(cascade = CascadeType.ALL)
@JoinTable(name="EMPLOYEE_ACCCOUNT", joinColumns = @JoinColumn(name="EMPLOYEE_ID"),
inverseJoinColumns = @JoinColumn(name="ACCOUNT_ID"))
private AccountEntity account;

Console:
Hibernate: insert into ACCOUNT (ACC_NUMBER) values (?)
Hibernate: insert into Employee (EMAIL, FIRST_NAME, LAST_NAME) values (?, ?, ?)
Hibernate: insert into EMPLOYEE_ACCCOUNT (ACCOUNT_ID, EMPLOYEE_ID) values (?, ?)
```

# 3. With shared primary key

-	In this technique, hibernate will ensure that it will use a common primary key value in both the tables. This way primary key of EmployeeEntity can safely be assumed the primary key of AccountEntity also.
-	 @PrimaryKeyJoinColumn is the main annotation to be used. 

```java
@OneToOne(cascade = CascadeType.ALL)
@PrimaryKeyJoinColumn
private AccountEntity account;

@OneToOne(mappedBy="account", cascade=CascadeType.ALL)
private EmployeeEntity employee;
```
```
Console:
Hibernate: insert into ACCOUNT (ACC_NUMBER) values (?)
Hibernate: insert into Employee (ACCOUNT_ID, EMAIL, FIRST_NAME, LAST_NAME) values (?, ?, ?, ?)
```

![]({{site.cdn}}/hibernate/onetoone-bidirectional.png)

![]({{site.cdn}}/hibernate/er-diagram-relationship-types.png)


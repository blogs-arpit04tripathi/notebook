---
layout: post
title: Association managed by single entity
permalink: /:collection/hibernate/associations/single-entity
---

```java
//Inside EmployeeEntity.java
@OneToOne
AccountEntity account;
 
//Inside AccountEntity.java
@OneToOne (mappedBy = "account")
EmployeeEntity employee;
```

Now to tell hibernate the association is managed by EmployeeEntity, we will add **‘mappedBy‘** attribute inside AccountEntity to make it manageable. Now to test above code we will have to set the association only once using "emp.setAccount(acc);" and employee entity is which is managing the relationship. AccountEntity does not need to know anything explicitly.

```java
emp.setAccount(acc);
//acc.setEmployee(emp);
sessionOne.save(acc); 
account.getEmployee().getEmployeeId()
```

You see that you do not need to tell anything to account entity (‘acc.setEmployee(emp)‘ is commented). Employee entity is managing the association both ways.

Another observation is regarding foreign key columns which we have only one now i.e. **account_ID** is Employee table. So no circular dependency as well. All good.

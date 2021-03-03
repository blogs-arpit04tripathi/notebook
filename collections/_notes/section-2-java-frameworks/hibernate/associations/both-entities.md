---
layout: post
title: Association managed by both entities
permalink: /:collection/hibernate/associations/both-entities
---


```java
//Inside EmployeeEntity.java
@OneToOne
AccountEntity account;
 
//Inside AccountEntity.java
@OneToOne
EmployeeEntity employee;

//acc.setEmployee(emp);
sessionOne.save(emp);
EmployeeEntity employee = (EmployeeEntity) sessionTwo.get(EmployeeEntity.class, genEmpId);
account.getEmployee().getEmployeeId()  
// throws null pointer exception
```

With above association, both ends are managing the association so both must be updated with information of each other using setter methods defined in entity java files. If you fail to do so, you will not be able to fetch the associated entity information and it will be returned as null.

```
Console Log output 
FIRST_NA2_1_0_,
            employeeen0_.LAST_NAME as LAST_NAM3_1_0_, accountent1_.ID as ID1_0_1_, accountent1_.ACC_NO as ACC_NO2_0_1_,
            accountent1_.employee_ID as employee3_0_1_, employeeen2_.ID as ID1_1_2_, employeeen2_.account_ID as 
account_4_1_2_,
            employeeen2_.FIRST_NAME as FIRST_NA2_1_2_, employeeen2_.LAST_NAME as LAST_NAM3_1_2_ from Employee
            employeeen0_ left outer join Account accountent1_ on employeeen0_.account_ID=accountent1_.ID
            left outer join Employee employeeen2_ on accountent1_.employee_ID=employeeen2_.ID where employeeen0_.ID=?
```

Both tables have foreign key association with column names **employee_ID** and **account_ID** respectively. It’s example of **circular dependency** in data and can easily bring down your application any time.

To correctly store above relationship, you must un-comment the line "acc.setEmployee(emp);". After uncommenting the line, you will be able to store and retrieve the association as desired but still there is circular dependency.

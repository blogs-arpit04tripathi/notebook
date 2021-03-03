---
layout: post
title: Composite Natural ID
permalink: /:collection/hibernate/annotations/composite-natural-id
---

```java
//Natural id part 1
   @NaturalId
   Integer seatNumber;
    
   //Natural id part 2
   @NaturalId
   String departmentName;

//Get the employee for natural id i.e. SSN; entity is not present in this session
      EmployeeEntity employee = (EmployeeEntity) sessionOne.byNaturalId(EmployeeEntity.class)
      .using("seatNumber", 12345)
      .using("departmentName", "IT")
      .load();
```

Entity fetching logic for composite natural id is same as simple natural id. No difference apart from use of multiple natural keys instead one.
```
Hibernate: insert into Employee (departmentName, FIRST_NAME, LAST_NAME, seatNumber, ID) values (?, ?, ?, ?, ?)
 
Hibernate: select employeeen_.ID as ID1_1_ from Employee employeeen_ where employeeen_.departmentName=? and employeeen_.seatNumber=?
 
Hibernate: select employeeen0_.ID as ID1_1_0_, employeeen0_.departmentName as departme2_1_0_, employeeen0_.FIRST_NAME as FIRST_NA3_1_0_,
employeeen0_.LAST_NAME as LAST_NAM4_1_0_, employeeen0_.seatNumber as seatNumb5_1_0_ from Employee employeeen0_ where employeeen0_.ID=?
```


---
layout: post
title: Annotation @zzz
permalink: /hibernate/annotations/natural-id
---

-	@Id annotation with @GeneratedValue to create primary keys for records in database. In most real life applications, these primary keys are **"artificial primary keys"** and referred only inside application runtime. However, there’s also the concept of a **"natural ID"**, which provides another convenient and logical way to refer to an entity, apart from an artificial or composite primary key.
-	**An example of natural id might be a Social Security number or a Tax Identification Number in the United States, and PAN number in India.** An entity (being a person or a corporation) might have an artificial primary key generated by Hibernate, but it also might have a unique tax identifier. Hibernate allows you to search and load entities based on these natural ids as well. For natural IDs, there are two forms of load mechanisms; one uses the simple natural ID (where the natural ID is one and only one field), and the other uses named attributes as part of a composite natural ID.

```java
@Entity
@Table(name = "Employee")
public class EmployeeEntity implements Serializable{
   private static final long serialVersionUID = -1798070786993154676L;
   @Id
   @Column(name = "ID", unique = true, nullable = false)
   private Integer           employeeId;    
   //Natural id can be SSN as well
   @NaturalId
   Integer SSN;
    
   //Setters and Getters
}
//Load the employee
      EmployeeEntity employee1 = (EmployeeEntity) sessionOne.load(EmployeeEntity.class, 1);
//Get the employee for natural id i.e. SSN; This does not execute another SQL SELECT as entity is already present in session
      EmployeeEntity employee2 = (EmployeeEntity) sessionOne.bySimpleNaturalId(EmployeeEntity.class).load(12345);
//Verify that employee1 and employee2 refer to same object
      assert(employee1 == employee2);
//Get the employee for natural id i.e. SSN; entity is not present in this session
      EmployeeEntity employee = (EmployeeEntity) sessionTwo.bySimpleNaturalId(EmployeeEntity.class).load(12345);
```
Please watch closely that in case of entity already not present in session, and if you get entity using it’s natural id then first primary id is fetched using natural id; and then entity is fetched using this primary id. **If entity is already present in session, then reference of same entity is returned** without executing additional SELECT statements in database.

```
Hibernate: select employeeen_.ID as ID1_1_ from Employee employeeen_ where employeeen_.SSN=?
 
Hibernate: select employeeen0_.ID as ID1_1_0_, employeeen0_.SSN as SSN2_1_0_, employeeen0_.FIRST_NAME as FIRST_NA3_1_0_,
employeeen0_.LAST_NAME as LAST_NAM4_1_0_ from Employee employeeen0_ where employeeen0_.ID=?
```

# How it works
If you look at logs then you will know that when you get an entity by its natural id then
1.	First primary key of entity is found by executing where clause of natural id
2.	This primary key is used fetch the information of entity

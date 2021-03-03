---
layout: post
title: Get Data by Lazy Loading
permalink: /:collection/hibernate/lazy-loading/get
---

In any application, hibernate fetches data from databse either in eager or lazy mode. **Hibernate lazy loading** refer to strategy when data is loaded lazily, on demand.

**Lazy loading** is a design pattern commonly used in computer programming to defer initialization of an object until the point at which it is needed. We know that in hibernate lazy loading can be done by specifying **"fetch= FetchType.LAZY"** in hibernate mapping annotations. e.g.
-	The point is that it is applied **only when you are defining mapping between two entities.** If above entity has been defined in DepartmentEntity then if you fetch DepartmentEntity then EmployeeEntity will be lazy loaded.
-	But, what if you want to lazy load DepartmentEntity itself i.e. **master entity itself should be lazy loaded.**
-	This problem can be solved by using **getReference()** method inside **IdentifierLoadAccess** class.

```java
@Entity
@Table(name = "Employee", uniqueConstraints = {
    @UniqueConstraint(columnNames = "ID"),
    @UniqueConstraint(columnNames = "EMAIL")
})
public class EmployeeEntity implements Serializable {

    private static final long serialVersionUID = -1798070786993154676 L;

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "ID", unique = true, nullable = false)
    private Integer employeeId;

    //Use the natural id annotation here
    @NaturalId(mutable = false)
    @Column(name = "EMAIL", unique = true, nullable = false, length = 100)
    private String email;

    @Column(name = "FIRST_NAME", unique = false, nullable = false, length = 100)
    private String firstName;

    @Column(name = "LAST_NAME", unique = false, nullable = false, length = 100)
    private String lastName;

    //Setters and Getters
    @ ManyToOne(fetch = FetchType.LAZY)
    @JoinColumns({
        @JoinColumn(name = "fname", referencedColumnName = "firstname"),
        @JoinColumn(name = "lname", referencedColumnName = "lastname")
    })
    public EmployeeEntity getEmployee() {
        return employee;
    }
}
```

I want to lazy load above master entity lazy loaded in my code i.e. I can get reference of entity in one place but might be actually needing it another place. Only when I need it, I want to initialize or load its data. Till the time, I want only the reference.

```java
//Get only the reference of EmployeeEntity for now
EmployeeEntity empGet = (EmployeeEntity) session.byId(EmployeeEntity.class).getReference(1);

System.out.println("No data initialized till now; Lets fetch some data..");

//Now EmployeeEntity will be loaded from database when we need it
System.out.println(empGet.getFirstName());
System.out.println(empGet.getLastName());
```


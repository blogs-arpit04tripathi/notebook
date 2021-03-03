---
layout: post
title: One to Many Mapping
permalink: /:collection/hibernate/mapping/one-to-many
---

This problem can be solved in two different ways.
1.	One is to have a **foreign key column** in account table i.e. EMPLOYEE_ID. This column will refer to primary key of Employee table. This way no two accounts can be associated with multiple employees. Obviously, account number needs to be unique for enforcing this restriction.
2.	Second approach is to have a common **join table** lets say EMPLOYEE_ACCOUNT. This table will have two column i.e. EMP_ID which will be foreign key referring to primary key in EMPLOYEE table and similarly ACCOUNT_ID which will be foreign key referring to primary key of ACCOUNT table.

# 1. With foreign key association

In this approach, both entity will be responsible for making the relationship and maintaining it.  
EmployeeEntity should declare that relationship is one to many, and AccountEntity should declare that relationship from its end is many to one.

![]({{site.cdn}}/hibernate/12Many-foreign-key.png)

```java
@Entity(name = "ForeignKeyAssoEntity")
@Table(name = "Employee", uniqueConstraints = {
@UniqueConstraint(columnNames = "ID"),
@UniqueConstraint(columnNames = "EMAIL") })
public class EmployeeEntity implements Serializable {
    	private static final long serialVersionUID = -1798070786993154676L;
	@OneToMany(cascade=CascadeType.ALL)
    	@JoinColumn(name="EMPLOYEE_ID")
    	private Set<AccountEntity> accounts;
}
```
```java
@Entity(name = "ForeignKeyAssoAccountEntity")
@Table(name = "ACCOUNT", uniqueConstraints = {@UniqueConstraint(columnNames = "ID")})
public class AccountEntity implements Serializable{
    private static final long serialVersionUID = -6790693372846798580L;
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "ID", unique = true, nullable = false)
    private Integer accountId;
 
    @Column(name = "ACC_NUMBER", unique = true, nullable = false, length = 100)
    private String accountNumber;
 
    @ManyToOne
    private EmployeeEntity employee;
}
```

# 2. with join table
This approach uses a join table to store the associations between account and employee entities. @JoinTable annotation has been used to make this association.

![]({{site.cdn}}/hibernate/12Many-join-table.png)

```java
@Entity(name = "JoinTableEmployeeEntity")
@Table(name = "Employee", uniqueConstraints = {
    @UniqueConstraint(columnNames = "ID"),
    @UniqueConstraint(columnNames = "EMAIL")
})
public class EmployeeEntity implements Serializable {
    private static final long serialVersionUID = -1798070786993154676 L;
    @OneToMany(cascade = CascadeType.ALL)
    @JoinTable(name = "EMPLOYEE_ACCOUNT",
        joinColumns = {
            @JoinColumn(name = "EMPLOYEE_ID", referencedColumnName = "ID")
        },
        inverseJoinColumns = {
            @JoinColumn(name = "ACCOUNT_ID", referencedColumnName = "ID")
        })
    private Set < AccountEntity > accounts;

    @Entity(name = "JoinTableAccountEntity")
    @Table(name = "ACCOUNT", uniqueConstraints = {
        @UniqueConstraint(columnNames = "ID")
    })
    public class AccountEntity implements Serializable {
        private static final long serialVersionUID = -6790693372846798580 L;
        @Id
        @GeneratedValue(strategy = GenerationType.IDENTITY)
        @Column(name = "ID", unique = true, nullable = false)
        private Integer accountId;

        @Column(name = "ACC_NUMBER", unique = true, nullable = false, length = 100)
        private String accountNumber;
    }
}
```


---
layout: post
title: Orphan Removal
permalink: /:collection/hibernate/cascade/orphan-removal
---

Apart from JPA provided cascade types, there is one more cascading operation in hibernate which is not part of the normal set above discussed, called **"orphan removal"**. This removes an owned object from the database when it’s removed from its owning relationship.

In our Employee and Account entity example, I have updated them as below and have mentioned **"orphanRemoval = true"** on accounts. It essentially means that whenever I will remove an ‘account from accounts set’ (which means I am removing the relationship between that account and Employee); the account entity which is not associated with any other Employee on database (i.e. orphan) should also be deleted.

```java
@Entity
@Table(name = "Employee")
public class EmployeeEntity implements Serializable{
    private static final long serialVersionUID = -1798070786993154676L;
    @Id
    @Column(name = "ID", unique = true, nullable = false)
    private Integer employeeId;
    @Column(name = "FIRST_NAME", unique = false, nullable = false, length = 100)
    private String firstName;
    @Column(name = "LAST_NAME", unique = false, nullable = false, length = 100)
    private String lastName;
 
    @OneToMany(orphanRemoval = true, mappedBy = "employee")
    private Set<AccountEntity> accounts;    
}
```

```java
@Entity (name = "Account")
@Table(name = "Account")
public class AccountEntity implements Serializable{
    private static final long serialVersionUID = 1L;
    @Id
    @Column(name = "ID", unique = true, nullable = false)
    @GeneratedValue(strategy = GenerationType.SEQUENCE)
    private Integer accountId;
    @Column(name = "ACC_NO", unique = false, nullable = false, length = 100)
    private String accountNumber;
 
    @ManyToOne
    private EmployeeEntity employee;
}
```


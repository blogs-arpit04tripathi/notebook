---
layout: post
title: JPA Cascading
permalink: /:collection/hibernate/jpa-cascade
---

We learned about **mapping associated entities** in hibernate already in previous tutorials such as **one-to-one mapping** and **one-to-many mappings**. There we wanted to save the mapped entity whenever relationship owner entity got saved. To enable this we had use "CascadeType" attribute.

Take a scenario where an Employee can have multiple Accounts; but one account must be associated with only one employee.

```java
@OneToMany(cascade=CascadeType.ALL, fetch = FetchType.LAZY)
@JoinColumn(name="EMPLOYEE_ID")
 private Set<AccountEntity> accounts;
```
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
 
    @OneToOne (mappedBy="accounts",  fetch = FetchType.LAZY)
    private EmployeeEntity employee;
}
```
**"cascade=CascadeType.ALL"** and it essentially means that any change happened on EmployeeEntity must cascade to AccountEntity as well. If you save an employee, then all associated accounts will also be saved into database. If you delete an Employee then all accounts associated with that Employee also be deleted. Simple enough.

But what if we only want to cascade only save operations but not delete operation. Then we need to clearly specify it using below code.
```java
@OneToMany(cascade=CascadeType.PERSIST, fetch = FetchType.LAZY)
@JoinColumn(name="EMPLOYEE_ID")
private Set<AccountEntity> accounts;
```
Now only when save() or persist() methods are called using employee instance then only accounts will be persisted. If any other method is called on session, it’s effect will not affect/cascade to accounts.

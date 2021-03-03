---
layout: post
title: Hibernate mapping Annotations
permalink: /:collection/hibernate/mapping-annotations
---

Hibernate supports JPA annotations and it has some other annotations in **org.hibernate.annotations** package. Some of the important JPA and hibernate annotations used are:

|||
|---|---|
|javax.persistence.Entity|	Used with model classes to specify that they are entity beans.|
|javax.persistence.Table|	Used with entity beans to define the corresponding table name in database.|
|javax.persistence.Access|	Used to define the access type, either field or property.<br>Default value is field and if you want hibernate to use getter/setter methods then you need to set it to property.|
|javax.persistence.Id|	Used to define the primary key in the entity bean.|
|javax.persistence.EmbeddedId|	Used to define composite primary key in the entity bean.|
|javax.persistence.Column|	Used to define the column name in database table.|
|javax.persistence.GeneratedValue|	Used to define the strategy to be used for generation of primary key.<br>Used in conjunction with javax.persistence.GenerationType enum.
|javax.persistence.OneToOne|	Used to define the one-to-one mapping between two entity beans. We have other similar annotations as OneToMany, ManyToOne and ManyToMany|
|javax.persistence.PrimaryKeyJoinColumn|	Used to define the property for foreign key. Used with org.hibernate.annotations .GenericGenerator and org.hibernate.annotations.Parameter|
|org.hibernate.annotations.Cascade|	Used to define the cascading between two entity beans, used with mappings. It works in conjunction with org.hibernate.annotations.CascadeType|

Here are two classes showing usage of these annotations.
```java
@Entity
@Table(name = "EMPLOYEE") 
/**@Table(name = "EMPLOYEE", uniqueConstraints = {
        @UniqueConstraint(columnNames = "ID"),
        @UniqueConstraint(columnNames = "EMAIL") })*/
@Access(value=AccessType.FIELD)
public class Employee {

	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	@Column(name = "emp_id")
	private long id;

	@Column(name = "emp_name") 
    	/**@Column(name = "emp_name", unique = false, nullable = false, length = 100)*/
	private String name;

	@OneToOne(mappedBy = "employee")
	@Cascade(value = org.hibernate.annotations.CascadeType.ALL)
	private Address address;

	//getter setter methods
}
```

```java
@Entity
@Table(name = "ADDRESS")
@Access(value = AccessType.FIELD)
public class Address {
    @Id
    @Column(name = "emp_id", unique = true, nullable = false)
    @GeneratedValue(generator = "gen")
    @GenericGenerator(name = "gen", strategy = "foreign", parameters = {
        @Parameter(name = "property", value = "employee")
    })
    private long id;

    @Column(name = "address_line1")
    private String addressLine1;

    @OneToOne
    @PrimaryKeyJoinColumn
    private Employee employee;
    //getter setter methods
}
```

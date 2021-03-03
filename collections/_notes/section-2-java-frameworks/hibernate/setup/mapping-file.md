---
layout: post
title: Hibernate Mapping File
permalink: /:collection/hibernate/mapping-file
---

**What is hibernate mapping file?**  
Hibernate mapping file is used to define the entity bean fields and database table column mappings. 
We know that JPA annotations can be used for mapping but sometimes XML mapping file comes handy when we are using third party classes and we can’t use annotations.

```xml
<!-- employee.hbm.xml -->
<?xml version='1.0' encoding='UTF-8'?>  
<!DOCTYPE hibernate-mapping PUBLIC  "-//Hibernate/Hibernate Mapping DTD 5.3//EN"  
 				"http://hibernate.sourceforge.net/hibernate-mapping-5.3.dtd">  
 <hibernate-mapping>  
  <class name="com.javatpoint.mypackage.Employee" table="emp1000">  
    <id name="id">  
     	<generator class="assigned"></generator>  
    </id>            
    <property name="firstName"></property>  
    <property name="lastName"></property>            
  </class>            
 </hibernate-mapping>
```

```java
StandardServiceRegistry ssr = new StandardServiceRegistryBuilder().configure("hibernate.cfg.xml").build();
Metadata meta = new MetadataSources(ssr).getMetadataBuilder().build();  
SessionFactory factory = meta.getSessionFactoryBuilder().build();  
Session session = factory.openSession();  
Transaction t = session.beginTransaction();   
Employee e1=new Employee();
e1.setId(101);
e1.setFirstName("Gaurav");
e1.setLastName("Chawla");        
session.save(e1);
t.commit();
factory.close();
session.close();
```

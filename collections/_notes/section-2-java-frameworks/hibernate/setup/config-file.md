---
layout: post
title: Hibernate Configuration File
permalink: /:collection/hibernate/config-file
---

**What is hibernate configuration file?**
-	Hibernate configuration file contains database specific configurations and used to initialize SessionFactory. 
-	We provide database credentials or JNDI resource information in the hibernate configuration xml file. 
-	Some other important parts of hibernate configuration file is Dialect information, so that hibernate knows the database type and mapping file or class details.

```xml
<!-- hibernate.cfg.xml -->
<?xml version='1.0' encoding='UTF-8'?>  
<!DOCTYPE hibernate-configuration PUBLIC  "-//Hibernate/Hibernate Configuration DTD 5.3//EN"  
          "http://hibernate.sourceforge.net/hibernate-configuration-5.3.dtd">  
<hibernate-configuration>  
    <session-factory>
        <property name="connection.driver_class">oracle.jdbc.driver.OracleDriver</property>
        <property name="connection.url">jdbc:oracle:thin:@localhost:1521:xe</property>  
        <property name="connection.username">system</property>  
        <property name="connection.password">jtp</property>
        <property name="connection.pool_size">10</property>
        <property name="hibernate.c3p0.min_size">10</property>
        <property name="dialect">org.hibernate.dialect.Oracle9Dialect</property>
        <property name="show_sql">true</property>
        <property name="hbm2ddl.auto">create</property>
        <property name="cache.provider_class">org.hibernate.cache.NoCacheProvider</property>
    <mapping resource="employee.hbm.xml"/>  
    </session-factory>    
</hibernate-configuration>  
```

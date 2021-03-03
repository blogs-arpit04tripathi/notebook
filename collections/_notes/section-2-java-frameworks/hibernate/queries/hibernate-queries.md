---
layout: post
title: Hibernate Queries
permalink: /:collection/hibernate/queries
---

**How to log hibernate generated sql queries in log files?**  
We can set below property for hibernate configuration to log SQL queries.
```xml
<property name="hibernate.show_sql">true</property>
```
However we should use it only in Development or Testing environment and turn it off in production environment.

**How to implement Joins in Hibernate?**  
There are various ways to implement joins in hibernate.
-	Using associations such as one-to-one, one-to-many etc.
-	Using JOIN in the HQL query. There is another form "join fetch" to load associated data simultaneously, no lazy loading.
-	We can fire native sql query and use join keyword.

**Can we execute native sql query in hibernate?**  
-	Hibernate provide option to execute native SQL queries through the use of SQLQuery object.
-	For normal scenarios, it is however not the recommended approach because we loose benefits related to hibernate association and hibernate first level caching. 

> (Read more at [Hibernate Native SQL Query Example]( http://www.journaldev.com/3422/hibernate-native-sql-query-example).)

**What is the benefit of native sql query support in hibernate?**  
Native SQL Query comes handy when we want to execute database specific queries that are not supported by Hibernate API such as query hints or the CONNECT keyword in Oracle Database.

**What is Named SQL Query?**  
-	Hibernate provides Named Query that we can define at a central location and use them anywhere in the code. We can created named queries for both HQL and Native SQL.
-	Hibernate Named Queries can be defined in Hibernate mapping files or through the use of JPA annotations @NamedQuery and @NamedNativeQuery.

**What are the benefits of Named SQL Query?**  
-	Hibernate Named Query helps us in grouping queries at a central location rather than letting them scattered all over the code.
-	Hibernate Named Query syntax is checked when the hibernate session factory is created, thus making the application fail fast in case of any error in the named queries.
Hibernate Named Query is global, means once defined it can be used throughout the application.
-	However one of the major disadvantage of Named query is that it’s hard to debug, because we need to find out the location where it’s defined.


---
layout: post
title: Problems ORM Solves
permalink: /:collection/hibernate/orm/problems-solved
---

# 1. Granularity
- Sometimes you will have an object model which has more classes than the number of corresponding tables in the database (Object model is more granular than the relational model). Take for example the notion of an Address.
- The greater the granularity, the deeper the level of detail. Granularity is usually used to characterize the scale or level of detail in a set of data.

# 2. Subtypes (inheritance)
Inheritance is a natural paradigm in object-oriented programming languages. However, RDBMSs do not define anything similar.

# 3. Identity
A RDBMS defines exactly one notion of 'sameness': the primary key. Java, however, defines both object identity a==b and object equality a.equals(b).

# 4. Associations
-	OOP associations - using references 
-	RDBMS associations - foreign key column.
-	If you need bidirectional relationships in Java, you must define the association twice. Likewise, you cannot determine the multiplicity of a relationship by looking at the object domain model.

# 5. Data navigation
-	The way you access data in Java is fundamentally different than the way you do it in a relational database. 
-	In Java, you navigate from one association to another walking the object network. This is not an efficient way of retrieving data from a relational database. You typically want to minimize the number of SQL queries and thus load several entities via JOINs and select the targeted entities before you start walking the object network.

---
layout: post
title: Hibernate HQL
permalink: /:collection/hibernate/hql
---

**What is HQL and what are it’s benefits?**
-	Hibernate Framework comes with a powerful object-oriented query language – Hibernate Query Language (HQL). It’s very similar to SQL except that we use Objects instead of table names, that makes it closer to OOP.
-	Hibernate query language is case-insensitive except for java class and variable names. So SeLeCT is the same as sELEct is the same as SELECT, but com.journaldev.model.Employee is not same as com.journaldev.model.EMPLOYEE.
-	The HQL queries are cached but we should avoid it as much as possible, otherwise we will have to take care of associations. However it’s a better choice than native sql query because of Object-Oriented approach. 

> (Read more at [HQL Example]( http://www.journaldev.com/2954/hibernate-query-language-hql-example-tutorial).)

**What is the benefit of Hibernate Criteria API?**  
Hibernate provides Criteria API that is more object oriented for querying the database and getting results. We can’t use Criteria to run update or delete queries or any DDL statements. It’s only used to fetch the results from the database using more object-oriented approach.

**Some of the common usage of Criteria API are:**
-	Criteria API provides Projection that we can use for aggregate functions such as sum(), min(), max() etc.
-	Criteria API can be used with ProjectionList to fetch selected columns only.
-	Criteria API can be used for join queries by joining multiple tables, useful methods are createAlias(), setFetchMode() and setProjection()
-	Criteria API can be used for fetching results with conditions, useful methods are add() where we can add Restrictions.
-	Criteria API provides addOrder() method that we can use for ordering the results.

> (Learn some quick examples at [Hibernate Criteria Example](http://www.journaldev.com/2963/hibernate-criteria-example-tutorial).)


---
layout: post
title: n+1 Select Problem
permalink: /:collection/hibernate/n+1-select-problem
---

Let's say you have a collection of Car objects (database rows), and each Car has a collection of Wheel objects (also rows). In other words, Car -> Wheel is a 1-to-many relationship.

Now, let's say you need to iterate through all the cars, and for each one, print out a list of the wheels. The naive O/R implementation would do the following:
```java
SELECT * FROM Cars;
And then for each Car:
SELECT * FROM Wheel WHERE CarId = ?
```
In other words, you have one select for the Cars, and then N additional selects, where N is the total number of cars.
Alternatively, one could get all wheels and perform the lookups in memory:

```sql
SELECT * FROM Wheel
```
This reduces the number of round-trips to the database from N+1 to 2. 

Most ORM tools give you several ways to prevent N+1 selects.
-	Basically, when using an ORM like NHibernate or EntityFramework, if you have a one-to-many (master-detail) relationship, and want to list all the details per each master record, you have to make N + 1 query calls to the database, "N" being the number of master records: 1 query to get all the master records, and N queries, one per master record, to get all the details per master record.
-	More database query calls --> more latency time --> decreased application/database performance.
    -	However, ORM's have options to avoid this problem, mainly using "joins".
-	This makes the first select and more 1 select by each N car, that's why it's called n+1 problem.
    -	To avoid this, make the association fetch as eager, so that hibernate loads data with a join.
    -	But attention, if many times you don't access associated Wheels, it's better to keep it LAZY or change fetch type with Criteria.

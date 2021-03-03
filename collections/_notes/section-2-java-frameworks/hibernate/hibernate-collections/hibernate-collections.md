---
layout: post
title: Hibernate Collections
permalink: /:collection/hibernate/collections
---

**What is difference between sorted collection and ordered collection, which one is better?**  
When we use Collection API sorting algorithms to sort a collection, it’s called sorted list. For small collections, it’s not much of an overhead but for larger collections it can lead to slow performance and OutOfMemory errors. Also the entity beans should implement Comparable or Comparator interface for it to work.

If we are using Hibernate framework to load collection data from database, we can use it’s Criteria API to use "order by" clause to get ordered list. Below code snippet shows you how to get it.

```java
List<Employee> empList = session.createCriteria(Employee.class).addOrder(Order.desc("id")).list();
```

Ordered list is better than sorted list because the actual sorting is done at database level, that is fast and doesn’t cause memory issues.

**What are the collection types in Hibernate?**  
There are five collection types in hibernate used for one-to-many relationship mappings.
-	Bag – List/ArrayList (Any order)
-	Bag semantic with ID – List/ArrayList (has ID)
-	Set - Set
-	List – List/ArrayList
-	Array - 
-	Map - Map

```sql
Case – 10 user, 10 vehicle, @ManyToMany
	Save(u1) // save(v1), save(v2) ……… , save(v10) 
	Save(u2) // save(v1), save(v2) ……… , save(v10)
	.
	.
	Save(u10) // save(v1), save(v2) ……… , save(v10)
// Here, cascading can be used.
```


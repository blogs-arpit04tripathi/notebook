---
layout: post
title: Query by example (QBE)
permalink: /:collection/hibernate/hql/criteria/query-by-example
---

In QBE, instead of programmatically building a Criteria object with Criterion objects and logical expressions, you can partially populate an instance of the object. You use this instance as a template and have Hibernate build the criteria for you based upon its values. 

For instance, if we have a user database, we can construct an instance of a user object, set the property values for type and creation date, and then use the Criteria API to run a QBE query. Hibernate will return a result set containing all user objects that match the property values that were set. Behind the scenes, Hibernate inspects the Example object and constructs an SQL fragment that corresponds to the properties on the Example object.

```java
Criteria crit = session.createCriteria(Supplier.class);
Supplier supplier = new Supplier();
supplier.setName("MegaInc");
crit.add(Example.create(supplier));
List results = crit.list();
```

Too many properties causing too many .add() hence use Query by Example.

Primary and null values are neglected while pulling up the data in the QBE.
- example.excludeProperty("userName");
- exampleUser.setUserName("User1%");
- example.enableLike();

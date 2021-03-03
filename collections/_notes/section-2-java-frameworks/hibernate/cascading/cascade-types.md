---
layout: post
title: JPA Cascade Types
permalink: /:collection/hibernate/cascade/types
---

The cascade types supported by the Java Persistence Architecture are as below:
1.	**CascadeType.PERSIST** : cascade type presist means that save() or persist() operations cascade to related entities.
2.	**CascadeType.MERGE** : cascade type merge means that related entities are merged when the owning entity is merged.
3.	**CascadeType.REFRESH** : cascade type refresh does the same thing for the refresh() operation.
4.	**CascadeType.REMOVE** : cascade type remove removes all related entities association with this setting when the owning entity is deleted.
5.	**CascadeType.DETACH** : cascade type detach detaches all related entities if a "manual detach" occurs.
6.	**CascadeType.ALL** : cascade type all is shorthand for all of the above cascade operations.

There is no **default cascade type in JPA**. By default no operations are cascaded.

![]({{site.cdn}}/hibernate/cascade-types.png)

The cascade configuration option accepts an array of CascadeTypes; thus, to include only refreshes and merges in the cascade operation for a One-to-Many relationship as in our example, you might see the following:
```java
@OneToMany(cascade={CascadeType.REFRESH, CascadeType.MERGE}, fetch = FetchType.LAZY)
@JoinColumn(name="EMPLOYEE_ID")
private Set<AccountEntity> accounts;
```
Above cascading will cause accounts collection to be only merged and refreshed.

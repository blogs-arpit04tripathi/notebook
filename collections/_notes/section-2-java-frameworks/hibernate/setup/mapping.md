---
layout: post
title: Hibernate Mapping
permalink: /:collection/hibernate/mapping
---

we can face situations where two entities can be related and must be referenced from each other, in either uni-direction or in bi-direction.

A common mistake by beginners, when designing entity models, is to try to make all associations bidirectional. Remember that associations that are not a natural part of the object model should not be forced into it. Hibernate Query Language (HQL) often proves a more natural way to access the required information when needed.

Ideally, we would like to dictate that only changes to one end of the relationship will result in any updates to the foreign key; and indeed, Hibernate allows us to do this by marking one end of the association as being managed by the other.

**In hibernate mapping associations, one (and only one) of the participating classes is referred to as "managing the relationship" and other one is called "managed by" using ‘mappedBy’ property. We should not make both ends of association "managing the relationship". Never do it.**

Note that "mappedBy" is purely about how the foreign key relationships between entities are saved. It has nothing to do with saving the entities themselves using cascade functionality.

While Hibernate lets us specify that changes to one association will result in changes to the database, it does not allow us to cause changes to one end of the association to be automatically reflected in the other end in the Java POJOs. We must use cascading capabilities for doing so.

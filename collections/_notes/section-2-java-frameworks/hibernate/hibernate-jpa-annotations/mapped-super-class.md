---
layout: post
title: Annotation @MappedSuperclass
permalink: /:collection/hibernate/annotations/mapped-super-class
---

-	A special case of inheritance occurs when the root of the hierarchy is not itself a persistent entity, but various classes derived from it are. Such a class can be abstract or concrete. The @MappedSuperclass annotation allows you to take advantage of this circumstance.
-	The class marked with @MappedSuperclass is not an entity, and is not query-able (it cannot be passed to methods that expect an entity in the Session or EntityManager objects). It cannot be the target of an association.
-	The mapping information for the columns of the superclass will be stored in the same table as the details of the derived class.


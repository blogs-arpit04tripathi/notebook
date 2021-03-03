---
layout: post
title: Annotation @Immutable
permalink: /:collection/hibernate/annotations/immutable
---

-	Marks an entity as being, well, immutable. 
-	useful for situations in which your entity represents reference data–things like lists of states, genders, or other rarely mutated data.

Since things like states tend to be rarely changed, someone usually updates the data manually, via SQL or an administration application. Hibernate can cache this data aggressively, which needs to be taken into consideration; if the reference data changes, you’d want to make sure that the applications using it are notified (may use refresh() method) or restarted somehow.

What @Immutable annotation tells Hibernate is that any updates to an immutable entity should not be passed on to the database without giving any error. @Immutable can be placed on a collection too; in this case, changes to the collection (additions, or removals) will cause a HibernateException to be thrown.


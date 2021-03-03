---
layout: post
title: Associations for Various Mappings
permalink: /:collection/hibernate/associations/various-mappings
---

Above example shows how to manage association between entities in one-to-one mapping. In above example, we could have chosen the association managed by **AccountEntity** as well and things would have worked out pretty well with minor code changes. But in case of other mappings (e.g. One-to-many or Many-to-one), you will not have the liberty to define associations at your will. You need rules.

Below table shows how you can select the side of the relationship that should be made the owner of a bi-directional association. **Remember that to make an association the owner, you must mark the other end as being mapped by the other.**

|TYPE OF ASSOCIATION|	OPTIONS/ USAGE|
|---|---|	
|One-to-one|	Either end can be made the owner, but one (and only one) of them should be; if you don’t specify this, you will end up with a circular dependency.|
|One-to-many|	The many end must be made the owner of the association.|
|Many-to-one|	This is the same as the one-to-many relationship viewed from the opposite perspective, so the same rule applies: the many end must be made the owner of the association.|
|Many-to-many|	Either end of the association can be made the owner.|

If this all seems rather confusing, just remember that **association ownership is concerned exclusively with the management of the foreign keys in the database** and that’s it.

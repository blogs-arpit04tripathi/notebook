---
layout: post
title: Annotation @NamedQuery and @NamedQueries
permalink: /:collection/hibernate/annotations/named-query
---

@NamedQuery and @NamedQueries allow one or more Hibernate Query Language or Java Persistence Query Language (JPQL) queries to be associated with an entity.

```java
@Entity
@NamedQuery(
        name="findAuthorsByName",
        query="from Author where name = :author"
)
public class Author {
...
}
```

If a query has no natural association with any of the entity declarations, it is possible to make the @NamedQuery annotation at the package level.

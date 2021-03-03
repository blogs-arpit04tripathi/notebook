---
layout: post
title: Spring Data
permalink: /:collection/spring/data/
---

- TOC
{:toc}

<hr><br>

# Introduction to Spring Data
***Spring Data JPA*** is a separate project within Spring Data ecosystem to enable you connect with persistent stores(SQL and NoSQL).

![spring-data]({{site.cdn}}/spring/spring-data/spring-data.png)

![spring-data-abstraction]({{site.cdn}}/spring/spring-data/spring-data-abstraction.png)

## Spring DATA JPA (Java Persistence API)

### Spring DATA JPA Features
- Support for Querydsl to create type-safe JPA queries
- Validation of @Query annotated queries at bootstrap time.
- @EnableJpaRepositories
- Advance Features
  - Extending and adding custom queries with JPQL
  - Query Domain Specific Language (Query DSL)
  - Defining custom methods (low-level coding)

### Adding JPA
- @Repository
- Extends JpaRepository<MyEntity, Long>
- List<ProductCategory> findByBestCategory(Boolean bestCategory), where bestCategory is a field(column)

```java
public interface EmployeeRepository extends JPARepositoty<Employee, Integer>{
    // findAll()
    // findById()
    // save()
    // deleteById()
}
```

# ORM(Object Relational Mapping)
- Map Entity classes into relational mapping.
- ORM framework does the query, transaction and mapping.
- JPA is specification to use ORM.

![orm]({{site.cdn}}/spring/spring-data/orm.png)

pom.xml
- Hibernate-core
- Hibernate entity manager

application.properties
- Datasource
- Hibernate.ddl-auto=update

Create POJO
- @Entity, @TableName, @MappedSuperClass
- @Column, @Id, 

@EntityScan(basePackages={"a","b"})

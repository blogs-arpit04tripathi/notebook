---
layout: post
title: Spring Data Rest
permalink: /:collection/spring/data-rest/
---


- `spring-data-rest`
- scans all JPARepositories, provides all basic crud features. 
- exposes REST api for each entity type for your JPARepository.

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-data-rest</artifactId>
</dependency>
```

- Spring data rest endpoints are HATEOAS compliant
  - HATEOAS - Hypermedia As the Engine of Application State
- Hypermedia driven sites provide information to access REST interfaces.
  - Think of it as metadata for REST data.
- HATEOAS uses HAL (Hypertext Application Language) data format. 
- For a collection, metadata includes page size, total elements, pages etc.
- Advance Features
  - Pagination, sorting and searching
  - Extending and adding custom queries with JPQL
  - Query Domain Specific Language (Query DSL)

```java
@RepositoryRestResource(path="members")
public interface EmployeeRepository extends JPARepositoty<Employee, Integer>{
    // findAll()
    // findById()
    // save()
    // deleteById()
}
```

```properties
spring.data.rest.base-path=/base
spring.data.rest.default-page-size=10
spring.data.rest.max-page-size=50
```

```
http://localhost:8080/employees?sort=lastname,firstname,asc
```

---
layout: post
title: Named Query
permalink: /:collection/hibernate/queries/named-queries
---

Named queries in hibernate is a **technique to group the HQL statements in single location**, and lately refer them by some name whenever need to use them. It **helps largely in code cleanup** because these HQL statements are no longer scattered in whole code.

Apart from above, below are some minor **advantages** of named queries:
1.	**Fail fast**: Their syntax is checked when the session factory is created, making the application fail fast in case of an error.
2.	**Reusable**: They can be accessed and used from several places which increase re-usability.

But, you must know that named query really **make code less readable and sometimes debugging becomes more hard**, as you have to locate the actual query definition being executed and understand that as well.

**Performance wise named queries done not make much difference**, nor put any excessive cost.
1.	The cost of transforming a HQL query to SQL is negligible compared to the cost of actually executing the query.
2.	The memory cost of caching the query is really small. Remember that Hibernate needs to have all the entities meta-data in memory anyway.

Named query definition has two important attributes:
- **name**: The name of name query by which it will be located using hibernate session.
- **query**: Here you give the HQL statement to get executed in database.

```java
@Entity
@Table(name = "DEPARTMENT", uniqueConstraints = {
    @UniqueConstraint(columnNames = "ID"),
    @UniqueConstraint(columnNames = "NAME")
})
@NamedQueries({
    @NamedQuery(name = DepartmentEntity.GET_DEPARTMENT_BY_ID, query = DepartmentEntity.GET_DEPARTMENT_BY_ID_QUERY),
    @NamedQuery(name = DepartmentEntity.UPDATE_DEPARTMENT_BY_ID, query = DepartmentEntity.UPDATE_DEPARTMENT_BY_ID_QUERY)
})
public class DepartmentEntity implements Serializable {

    static final String GET_DEPARTMENT_BY_ID_QUERY = "from DepartmentEntity d where d.id = :id";
    public static final String GET_DEPARTMENT_BY_ID = "GET_DEPARTMENT_BY_ID";

    static final String UPDATE_DEPARTMENT_BY_ID_QUERY = "UPDATE DepartmentEntity d SET d.name=:name where d.id = :id";
    public static final String UPDATE_DEPARTMENT_BY_ID = "UPDATE_DEPARTMENT_BY_ID";

    private static final long serialVersionUID = 1 L;

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    @Column(name = "ID", unique = true, nullable = false)
    private Integer id;
}

//Update record using named query
Query query = session.getNamedQuery(DepartmentEntity.UPDATE_DEPARTMENT_BY_ID)
    .setInteger("id", 1).setString("name", "Finance");
query.executeUpdate();
//Get named query instance
query = session.getNamedQuery(DepartmentEntity.GET_DEPARTMENT_BY_ID).setInteger("id", 1);
//Get all departments (instances of DepartmentEntity)
DepartmentEntity department = (DepartmentEntity) query.uniqueResult();
```

**Important points:**
1.	Use JPA style query language. e.g. in place of table name, use Entity name.
2.	Use named queries preferably only for selecting records based on complex conditions. Do not use them excessively, otherwise there is no use of using ORM over simple JDBC.
3.	Please remember that result of named queries is not cached in secondary cache, only query object itself get cached.
4.	Make a habit of adding couple of unit testcases whenever you add any named query in code. And run those unit testcases immediately.
5.	You can not have two named queries with same name in hibernate. Hibernate shows fail fast behavior in this regard and will show error in application start up itself.

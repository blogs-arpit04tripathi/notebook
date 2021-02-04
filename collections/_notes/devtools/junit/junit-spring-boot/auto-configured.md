---
layout: post
title: Auto-Configured Tests
permalink: /:collection/junit/spring-boot/auto-configured
---

One of the amazing features of Spring Boot’s auto-configured annotations is that it helps to load parts of the complete application and test specific layers of the codebase.

**Few widely used annotations**

|||
|---|---|
|@WebFluxTest|Used to test Spring Webflux controllers. It’s often used along with @MockBean to provide mock implementations for required dependencies.|
|@JdbcTest|Used to test JPA applications but it’s for tests that only require a DataSource. The annotation configures an in-memory embedded database and a JdbcTemplate.|
|@JooqTest|To test jOOQ-related tests, this annotation configures a DSLContext.|
|@DataMongoTest| To test MongoDB applications. By default, it configures an in-memory embedded MongoDB if the driver is available through dependencies, configures a MongoTemplate, scans for @Document classes, and configures Spring Data MongoDB repositories.|
|@DataRedisTest|Used to test Redis applications. It scans for @RedisHash classes and configures Spring Data Redis repositories by default.|
|@DataLdapTest|configures an in-memory embedded LDAP (if available), configures a LdapTemplate, scans for @Entry classes, and configures Spring Data LDAP repositories by default.|
|@RestClientTest|Used to test REST clients. It auto-configures different dependencies like Jackson, GSON, and Jsonb support, configures a RestTemplateBuilder, and adds support for MockRestServiceServer by default.|

> The complete source code of this article can be [found over on GitHub](https://github.com/eugenp/tutorials/tree/master/spring-boot).
> And, if you want to keep learning about testing – we have separate articles related to [integration tests](https://www.baeldung.com/integration-testing-in-spring) and [unit tests in JUnit 5](https://www.baeldung.com/junit-5).

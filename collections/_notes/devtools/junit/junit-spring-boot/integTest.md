---
layout: post
title: Integration Testing with @SpringBootTest
permalink: /:collection/junit/spring-boot/integTest
---

**Integration Tests**
* focus on integrating different layers of the application.
* That also means no mocking is involved.
* Ideally, we should keep the integration tests separated from the unit tests and should not run along with the unit tests. 
    - Can be done by using a different profile to only run the integration tests.
    - ***Reason*** : Integration tests are time-consuming and might need an actual database to execute.

> Integration tests need to start up a container to execute the test cases, which needs extra setup.

`@SpringBootTest` annotation

* used when we need to bootstrap the entire container
* creating the ApplicationContext that will be utilized in our tests.
* `webEnvironment` attribute configures runtime environment
    - we’re using WebEnvironment.MOCK - container will operate in a mock servlet environment.

`@TestPropertySource` annotation

* configure locations of properties files specific to our tests.
* property file loaded with `@TestPropertySource` will override the existing application.properties file.

```properties
# application-integrationtest.properties
spring.datasource.url = jdbc:h2:mem:test
spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.H2Dialect
```

```java
@RunWith(SpringRunner.class)
@SpringBootTest(SpringBootTest.WebEnvironment.MOCK, classes = Application.class)
@AutoConfigureMockMvc
@TestPropertySource(locations = "classpath:application-integrationtest.properties")
public class EmployeeRestControllerIntegrationTest {

    @Autowired
    private MockMvc mvc;
    @Autowired
    private EmployeeRepository repository;

    @Test
    public void givenEmployees_whenGetEmployees_thenStatus200() throws Exception {
        createTestEmployee("bob");
        mvc.perform(get("/api/employees")
                .contentType(MediaType.APPLICATION_JSON))
            .andExpect(status().isOk())
            .andExpect(content().contentTypeCompatibleWith(MediaType.APPLICATION_JSON))
            .andExpect(jsonPath("$[0].name", is("bob")));
    }
}
```

Test cases for the integration tests might look similar to the Controller layer unit tests, but for IntegrationTest nothing is mocked and end-to-end scenarios will be executed.

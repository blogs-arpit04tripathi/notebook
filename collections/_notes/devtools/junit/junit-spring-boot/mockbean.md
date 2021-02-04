---
layout: post
title: Mocking with @MockBean
permalink: /:collection/junit/spring-boot/mockbean
---

For Unit Testing, Service layer needs to be independent of repository layer implementation.

`@MockBean` annotation
* It [creates a Mock](https://www.baeldung.com/mockito-mock-methods) for the EmployeeRepository which can be used to bypass the call to the actual EmployeeRepository.

`@TestConfiguration` annotation
* To check the Service class, instance needs to be created and available as a @Bean in order to @Autowire it.
* Spring Boot annotation that can be used on classes in src/test/java to indicate that they should not be picked up by component scanning.

```java
@RunWith(SpringRunner.class)
public class EmployeeServiceImplIntegrationTest {

    @TestConfiguration
    static class EmployeeServiceImplTestContextConfiguration {
        @Bean
        public EmployeeService employeeService() {
            return new EmployeeServiceImpl();
        }
    }

    @Autowired
    private EmployeeService employeeService;
    @MockBean
    private EmployeeRepository employeeRepository;

    @Before
    public void setUp() {
        Employee alex = new Employee("alex");
        Mockito.when(employeeRepository.findByName(alex.getName()))
            .thenReturn(alex);
    }

    @Test
    public void whenValidName_thenEmployeeShouldBeFound() {
        String name = "alex";
        Employee found = employeeService.getEmployeeByName(name);
        assertThat(found.getName()).isEqualTo(name);
    }
}
```

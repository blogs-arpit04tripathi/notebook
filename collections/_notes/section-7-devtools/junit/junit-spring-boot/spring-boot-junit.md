---
layout: post
title: Testing Spring Boot
permalink: /:collection/junit/spring-boot
---


***spring-boot-starter-test dependency***

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
    <version>2.0.4.RELEASE</version>
</dependency>
```
for practice add h2 DB (in-memory DB)

***Entity Definition***

```java
@Entity
@Table(name = "person")
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private Long id;
    @Size(min = 3, max = 20)
    private String name;
    // standard getters and setters, constructors
}
```

***Repository Definition***

```java
@Repository
public interface EmployeeRepository extends JpaRepository<Employee, Long> {
     public Employee findByName(String name);
}
```

***Service Implementation Definition***

```java
@Service
public class EmployeeServiceImpl implements EmployeeService {
    @Autowired
    private EmployeeRepository employeeRepository;
    @Override
    public Employee getEmployeeByName(String name) {
        return employeeRepository.findByName(name);
    }
}
```

***Controller Definition***

```java
@RestController
@RequestMapping("/api")
public class EmployeeRestController { 
    @Autowired
    private EmployeeService employeeService; 
    @GetMapping("/employees")
    public List<Employee> getAllEmployees() {
        return employeeService.getAllEmployees();
    }
}
```

Integration Testing with `@DataJpaTest`
```java
@RunWith(SpringRunner.class)
@DataJpaTest
public class EmployeeRepositoryIntegrationTest {
    @Autowired
    private TestEntityManager entityManager;
    @Autowired
    private EmployeeRepository employeeRepository;

    @Test
    public void whenFindByName_thenReturnEmployee() {
        // given
        Employee alex = new Employee("alex");
        entityManager.persist(alex);
        entityManager.flush();
        // when
        Employee found = employeeRepository.findByName(alex.getName());
        // then
        assertThat(found.getName()).isEqualTo(alex.getName());
    }
}
```

* `@RunWith(SpringRunner.class)` is used to provide a bridge between Spring Boot test features and JUnit. 
* `@DataJpaTest` provides some standard setup needed for testing the persistence layer:
    - configuring H2, an in-memory database
    - setting Hibernate, Spring Data, and the DataSource
    - performing an `@EntityScan`
    - turning on SQL logging
* `TestEntityManager` provided by Spring Boot
    - to setup data in our database
    - alternative to the standard `JPAEntityManager` that provides methods commonly used when writing tests.

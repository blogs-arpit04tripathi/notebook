---
layout: post
title: Unit Testing with @WebMvcTest
permalink: /:collection/junit/spring-boot/webmvctest
---

Mock the Service layer code for our unit tests of `@Controller`.

`@WebMvcTest` annotation
* auto-configure the Spring MVC infrastructure for our unit tests.
* Mostly @WebMvcTest will be limited to bootstrap a single controller. 
* used along with @MockBean to provide mock implementations for required dependencies.
* also auto-configures `MockMvc` which offers a powerful way of easy testing MVC controllers without starting a full HTTP server.

```java
@RunWith(SpringRunner.class)
@WebMvcTest(EmployeeRestController.class)
public class EmployeeRestControllerIntegrationTest {
    
    @Autowired
    private MockMvc mvc;
    @MockBean
    private EmployeeService service;

    @Test
    public void givenEmployees_whenGetEmployees_thenReturnJsonArray() throws Exception {
        Employee alex = new Employee("alex");
        List < Employee > allEmployees = Arrays.asList(alex);
        given(service.getAllEmployees()).willReturn(allEmployees);
        mvc.perform(get("/api/employees")
                .contentType(MediaType.APPLICATION_JSON))
            .andExpect(status().isOk())
            .andExpect(jsonPath("$", hasSize(1)))
            .andExpect(jsonPath("$[0].name", is(alex.getName())));
    }
}
```

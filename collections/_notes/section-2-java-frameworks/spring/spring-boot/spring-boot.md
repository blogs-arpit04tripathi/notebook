---
layout: post
title: Spring Boot
permalink: /:collection/spring/boot/
---

- TOC
{:toc}

<hr><br>
 
# Spring Boot Basics

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class SpringBootWebApplication {
    public static void main(String[] args) throws Exception {
        SpringApplication.run(SpringBootWebApplication.class, args);
    }
}
```

### @SpringBootApplication
`@Configuration`, `@EnableAutoConfiguration` and `@ComponentScan` with their default attributes.
- **exclude**: Exclude the list of classes from the auto configuration.
- **excludeNames**: Exclude the list of fully qualified class names from the auto configuration.
- **scanBasePackageClasses**: Provide the list of classes that has to be applied for the @ComponentScan.
- **scanBasePackages** Provide the list of packages that has to be applied for the @ComponentScan.

### @EnableConfigurationProperties
- Enable the pre configured properties.
- To override them, edit `application.properties` or `application.yaml`.
- `src/main/resources` directory
- auto detected without any spring based configurations 
- Property based configuration (PropertySource)
- all default properties given by spring boot here: [Common application properties]( https://docs.spring.io/spring-boot/docs/current/reference/html/appendix-application-properties.html)

### @EnableAutoConfiguration
- Auto-configures the beans that are present in the classpath. 
- For example, for tomcat-embedded.jar in the classpath, then you will need a TomcatEmbeddedServletContainerFactory bean to configure the tomcat server. This will be searched and configured without any manual XML configurations.
- For example, it will be used when scanning for [@Entity]( https://javabeat.net/spring-data-jpa-namedquery/) classes. 
- It is generally recommended that you place @EnableAutoConfiguration in a root package so that all sub-packages and classes can be searched.
- Auto-configuration classes are normal `@Configuration` annotated classes only. These are mentioned in the `spring.factories` file. Spring checks the spring.factories files under the folder META-INF in your project or JAR file to auto-configure the configuration classes.
- Parameters – exclude, excludes

### SpringApplication.run(SpringBootWebApplication.class, args)
- static method of class SpringApplication
- source as the class with @SpringBootApplication - SpringBootWebApplication
- sets up default configuration
- starts spring application context
- performs classpath scan
- starts tomcat server

**How to check all the loaded beans?**  
```java
@Override
public void run(String... args) throws Exception { 
    String[] beans = applicationContext.getBeanDefinitionNames();
    for (String bean : beans) {
        System.out.println(bean);
    }
}
```

**Write Custom Auto-Configuration?**  
> Read more about [spring boot custom auto-configuration](https://www.baeldung.com/spring-boot-custom-auto-configuration)

```java
@Configuration
@ConditionalOnClass({ String.class })
public class MyAutoconfiguration {
	Logger logger = LoggerFactory.getLogger(MyAutoconfiguration.class);
	@Bean
	public String cacheManager() {
		logger.info("Configure Defaults");
		return new String("test");
	}
}
```

Create spring.factories file as below and put it under the resources/META-INF folder:
```properties
org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
com.autoconfiguration.MyAutoconfiguration
```
- `@AutoConfigureOrder(Ordered.HIGHEST_PRECEDENCE)`, If we want our auto-configuration class to have priority over other auto-configuration candidates.

**How to disable a specific auto-configuration?**  
```java
// other annotations
@EnableAutoConfiguration(exclude = DataSourceAutoConfiguration.class)
public class MyConfiguration { }

// other annotations
@SpringBootApplication(exclude = DataSourceAutoConfiguration.class)
public class MyConfiguration { }

//exclude using properties file
spring.autoconfigure.exclude=org.springframework.boot.autoconfigure.jdbc.DataSourceAutoConfiguration
```

**How to tell an auto-configuration to back away when a bean exists?**  
To instruct an auto-configuration class to back off when a bean is already existent, we can use the `@ConditionalOnMissingBean` annotation. The most noticeable attributes of this annotation are:
- **value** : The types of beans to be checked
- **name**  : The names of beans to be checked

When placed on a method adorned with @Bean, the target type defaults to the method’s return type:

```java
@Configuration
public class CustomConfiguration {
    @Bean
    @ConditionalOnMissingBean
    public CustomService service() { ... }
}
```

# Property Binding

- Spring Boot allows you to externalize your configuration so you can work with the same application code in different environments. 
- You can use properties files, YAML files, environment variables and command-line arguments to externalize configuration.
- Property values can be injected directly into your beans using
    - **@Value** annotation, accessed via Spring’s Environment abstraction or 
    - bound to structured objects via **@ConfigurationProperties**.

### Type-safe configuration properties
- `@Value("${property.name}")` is used to inject property values one by one.
- Cumbersome if you are working with multiple properties or your data is hierarchical in nature. 
- Spring Boot provides an alternative method of working with properties that allows strongly typed beans to govern and validate the configuration of your application.

### Relaxed binding
Spring Boot automatically uses relaxed rules for binding Environment properties to **@ConfigurationProperties** beans. Meaning, there doesn’t need to be an exact match between the Environment property name and the bean property name. Imagine you have a bean property called allowCredentials you can use the following configuration in your properties.
- **allowCredentials** : using standard camel case syntax.
- **allow-credentials** : using dashed notation.
- **allow_credentials** : using underscore notation.
- **ALLOW_CREDENTIALS** : using upper case format.

```properties
cmdb.resource-url=http://java2novice.com
cmdb.resourcePort[0]=80
cmdb.resourcePort[1]=443
cmdb.resourceCount=10
```

**property binding with @ConfigurationProperties**  
```java
@Configuration
@ConfigurationProperties("cmdb")
public class CmdbProperties {
    @NotEmpty
    private String resourceUrl;

    private List<Integer> resourcePort;
    
    @Max(5)
    @Min(0)
    private Integer resourceCount;

// Output
Property: cmdb.resourceCount
    Value: 10
    Reason: must be less than or equal to 5
```

**property binding with @Value**  
```java
// or use @Value for individual properties
@Value("${cmdb.resource-url}")
private int threadPool;
```

### @ConfigurationProperties vs @Value
![configurationProperties_vs_value]({{site.cdn}}/spring/spring-boot/configurationProperties_vs_value.png)

- If you define a set of configuration keys for your own components, spring boot recommends you to group them in a POJO annotated with @ConfigurationProperties.

## Load external property files

By default, Spring Boot look for externalized default property file `application.properties` into given below predetermined locations:
- In the classpath root.
- In the package "/config" in classpath.
- In the current directory.
- In the "/config" directory of current folder.

```properties
# SPRING CONFIG - using environment property only (ConfigFileApplicationListener)
spring.config.additional-location= # Config file locations used in addition to the defaults.
spring.config.location= # Config file locations that replace the defaults.
spring.config.name=application # Config file name.

spring.config.name=application,myapp
spring.config.location=classpath:/data/myapp/config,classpath:/data/myapp/external/config
```

## Spring boot property resolution order

Spring Boot uses a very particular PropertySource order that is designed to allow sensible overriding of values.

**Properties are considered in the following order**  
1.	Devtools global settings properties on your home directory (~/.spring-boot-devtools.properties when devtools is active).
2.	@TestPropertySource annotations on your tests.
3.	@SpringBootTest#properties annotation attribute on your tests.
4.	Command line arguments.
5.	Properties from SPRING_APPLICATION_JSON (inline JSON embedded in an environment variable or system property)
6.	ServletConfig init parameters.
7.	ServletContext init parameters.
8.	JNDI attributes from java:comp/env.
9.	Java System properties (System.getProperties()).
10.	OS environment variables.
11.	A RandomValuePropertySource that only has properties in random.*.
12.	Profile-specific application properties outside of your packaged jar (application-{profile}.properties and YAML variants)
13.	Profile-specific application properties packaged inside your jar (application-{profile}.properties and YAML variants)
14.	Application properties outside of your packaged jar (application.properties and YAML variants).
15.	Application properties packaged inside your jar (application.properties and YAML variants).
16.	@PropertySource annotations on your @Configuration classes.
17.	Default properties (specified using SpringApplication.setDefaultProperties).

## Profile Based properties

Lets consider following profiles:
- dev for your local development settings
- staging for your staging server settings
- prod for your production settings
- test for running your tests

### Multiple Profiles in SpringBoot 
#### Option1 - properties file
- application.properties
- application-test.properties
- application-stg.properties
- application-prod.properties

```cmd
mvn spring-boot:run -Dspring.profiles.active=qa
```

#### Option2 - For YAML
```
spring.profiles.active=dev
---
spring.profiles=dev
---
spring.profiles=qa
```

### YAML
- indentation based properties.
- Used as alternative to application.properties
- Snake YAML dependency in classpath with YAML.
- Cannot use `@PropertySource` annotation

Spring classes to Load YAML documents
- YamlPropertiesFactoryBean as properties
- YamlMapFactoryBean as map

**What do you know about YAML in the realm of Microservices?**  
- Individual legible language (readable)
- YAML file is more organized, less confusing and hence it provides easy accessibility to a variety of web developers.
- YAML possesses the hierarchical form of data hence helping with swift development of various applications.
- used to externalize properties of microservices in various environments.

**Shed light on the various aspects of using Spring Profiles**  
In the context of Microservices, the Spring Profiles play an essential role. It is so because it allows the users in the process of registering various beans.

However, the registration process of beans is always dependent on various ways by which the application has been executed. Hence, if you are running the application in the DEVELOPMENT mode, you would witness that a certain number of items can be encumbered in an easy manner. On the other hand, during the time of production, the other items can also be loaded.

With the widespread use of Spring Boot, it has become relatively quite easy to make sure that all the profiles can be easily booted. This makes sure that the developed application is running free of errors and is light on the interface.

# Basic Configurations

### Default properties file
- application.properties (src/main/resources)

### Embedded Server
* Application are deployable by just running, server embedded as deployable unit.
* For deployment you need,
	- War file
	- App Server
	- Deployment Script or tools like jenkins
* Advantage
	- Microservice architecture compatible
	- Standalone app works as a unit
    - Quickly testable

### Run SpringBoot application as external WAR Files

- changes in pom.xml - packaging as war and tomcat as provided

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>apring-boot-starter-tomcat</artifactId>
    <scope>provided</scope>
</dependency>
```
* extends `SpringBootServletInitializer` and override *configure* method.
* Different values of scope and its meaning

### Hierarchal Properties
* @ConfigurationProperties("root")
* Add private member variables with name name for root.name property
* Use this class with @Autowired.

# Logging

# Spring Boot Spring Data JPA

- JPA is a way to use ORM (Object Relational Mapping)
- Spring Data JPA is the spring module to work with JPA in spring projects.
- JPA(Java Persistence API) are specifications defining set of interfaces.
- In spring-boot, hibernate is default implementation of JPA.
- EntityManager is similar to hibernate SessionFactory.
- EntityManager can serve as a wrapper for a hibernate session object.
- we can inject the EntityManager into our DAO.

**DataSource**
- spring-boot-starter-data-jpa
- Oracle Driver (ojdbc7.jar)
- HikariCP 2.6 (to maintain connection pool)
- For in-memory DB, you can add Apache Derby or H2 dependency
- No need to give JDBC Driver class name, spring-boot will automatically detect it based on url.

```xml
<!-- dependencies -->
<artifactId>spring-boot-starter-data-jpa</artifactId>
<artifactId>mysql-connector-java</artifactId>
<artifactId>ojdbc7</artifactId>
<artifactId>spring-boot-configuration-processor</artifactId>
```
```properties
# Oracle DB Settings
spring.datasource.url=jdbc:oracle:thin:@localhost:1521:empdb
spring.datasource.username=my_prod_user
spring.datasource.password=my_db_password
spring.datasource.driver-class-name=oracle.jdbc.driver.OracleDriver
# MySql DB configuration
spring.mysql.datasource.url=jdbc:mysql://localhost:3306/branch_db?autoReconnect=true&useSSL=false
spring.mysql.datasource.username=my_user
spring.mysql.datasource.password=my_password
spring.mysql.datasource.driver-class-name=com.mysql.jdbc.Driver
# HikariCP settings Connection Pooling
spring.datasource.hikari.connection-timeout=30000
spring.datasource.hikari.maximum-pool-size=50
```

**oracle db**  
```java
@Configuration
@EnableTransactionManagement
@EnableJpaRepositories(
    entityManagerFactoryRef = "oraclesqlEntityManager",
    transactionManagerRef = "oraclesqlTransactionManager",
    basePackages = "com.java2novice.springboot.dao.oraclesql"
)
public class OracleSqlConfiguration {
 
    @Bean
    @Primary
    @ConfigurationProperties(prefix = "spring.oraclesql.datasource")
    public DataSource oraclesqlDataSource() {
        return DataSourceBuilder.create().build();
    }
 
    @Primary
    @Bean(name = "oraclesqlEntityManager")
    public LocalContainerEntityManagerFactoryBean oraclesqlEntityManagerFactory(EntityManagerFactoryBuilder builder) {
        return builder
            .dataSource(oraclesqlDataSource())
            .packages(Employee.class) // you can also give the package where the Entities are given rather than giving Entity class
            .persistenceUnit("oraclesqlPU")
            .build();
    }
 
    @Primary
    @Bean(name = "oraclesqlTransactionManager")
    public PlatformTransactionManager oraclesqlTransactionManager(@Qualifier("oraclesqlEntityManager") EntityManagerFactory entityManagerFactory) {
        return new JpaTransactionManager(entityManagerFactory);
    }
}
```

**mysql**
```java
@Configuration
@EnableTransactionManagement
@EnableJpaRepositories(
    entityManagerFactoryRef = "mysqlEntityManager",
    transactionManagerRef = "mysqlTransactionManager",
    basePackages = "com.java2novice.springboot.dao.mysql"
)
public class MySqlConfiguration {
 
    @Bean
    @ConfigurationProperties(prefix = "spring.mysql.datasource")
    public DataSource mysqlDataSource() {
        return DataSourceBuilder.create().build();
    }
 
    @Primary
    @Bean(name = "mysqlEntityManager")
    public LocalContainerEntityManagerFactoryBean mysqlEntityManagerFactory(EntityManagerFactoryBuilder builder) {
        return builder
            .dataSource(mysqlDataSource())
            .packages(Branch.class)
            .persistenceUnit("mysqlPU")
            .build();
    }
 
    @Primary
    @Bean(name = "mysqlTransactionManager")
    public PlatformTransactionManager mysqlTransactionManager(@Qualifier("mysqlEntityManager") EntityManagerFactory entityManagerFactory) {
        return new JpaTransactionManager(entityManagerFactory);
    }
}
```

**@Configuration**: indicate that class declares @Bean methods to be processed by the Spring container to be used at runtime.  
**@EnableTransactionManagement**: used to allow the usage of annotation-driven transaction management capability.  
**@EnableJpaRepositories**: since we are using spring data jpa, this annotation is required to tell Spring to enable JPA repositories. We specified the entityManagerFactory and the transactionManager beans to be used in the JPA repositories.  
**@ConfigurationProperties**: This annotation tells spring to pick up the data source properties that are prefixed with "spring.oraclesql.datasource" from the application.properties file and build a data source using DataSourceBuilder.  
**@Primary**: Basically tell the spring that the configured data source is primary.  

```properties
#this line shows the sql statement in the logs
logging.level.org.hibernate.SQL=debug
#this line shows sql values in the logs
logging.level.org.hibernate.type.descriptor.sql=trace
```
```java
@Entity
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.SEQUENCE, generator = "emp_seq")
    @SequenceGenerator(sequenceName = "emp_seq", allocationSize = 1, name = "emp_seq")
    @Column(name = "emp_id")
    private String empId;
    private String name;
}

@Repository
public interface EmployeeRepository extends CrudRepository<Employee, String>{
    // All default CRUD operations are in the implementation class provided by spring-data-jpa
    // custom find by filter
    List<Employee> findByName(String name);
    // implementation provided by JPA if naming convention followed, findByProperty
    // for direct member variable --> findByName
    // for object type member variable --> findByAddressPincode, Address object with field pincode
}
```

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-data-rest</artifactId>
</dependency>
```

# Spring Boot Embedded Containers

Whenever you are creating a Java application, deployment can be done via two methods:
- Using an application container that is external.
- Embedding the container inside your jar file.

### Why Embedded Tomcat Server
- Convenience
- Servlet config is now application config, can be changed with application.properties ex. port number.
- Standalone application.
- useful for microservices architecture.

Spring Boot contains Jetty, Tomcat, and Undertow servers, all of which are embedded.
- **Jetty** – Used in a wide number of projects, Eclipse Jetty can be embedded in framework, application servers, tools, and clusters.
- **Tomcat** – Apache Tomcat is an open source JavaServer Pages implementation which works well with embedded systems.
- **Undertow** – A flexible and prominent web server that uses small single handlers to develop a web server.

**How to deploy Spring Boot web applications as JAR and WAR files?**  
```
web application --> package as WAR file --> deploy into an external server
```
- Doing this allows us to arrange multiple applications on the same server. During the time that CPU and memory were scarce, this was a great way to save resources.  

- Computer hardware is fairly cheap now, and the attention has turned to server configuration. A small mistake in configuring the server during deployment may lead to catastrophic consequences.
- **Spring tackles this problem by providing a plugin, namely spring-boot-maven-plugin, to package a web application as an executable JAR**. To include this plugin, just add a plugin element to pom.xml:

```xml
<plugin>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-maven-plugin</artifactId>
</plugin>
```
- With this plugin in place, we’ll get a fat JAR after executing the package phase. This JAR contains all the necessary dependencies, including an embedded server. Thus, we no longer need to worry about configuring an external server.
- We can then run the application just like we would an ordinary executable JAR.

```xml
<packaging>war</packaging> //Default is jar
```
And leave the container dependency off the packaged file:
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-tomcat</artifactId>
    <scope>provided</scope>
</dependency>
```
- After executing the Maven package phase, we’ll have a deployable WAR file.

# SpringBoot DevTools

> Read more about [Spring Boot DevTools]( https://www.baeldung.com/spring-boot-devtools).

Spring Boot Developer Tools, or DevTools, is a set of tools making the development process easier.
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
</dependency>
```

- The spring-boot-devtools module is automatically disabled if the application runs in production. The repackaging of archives also excludes this module by default. Hence, it won’t bring any overhead to our final product.
- By default, DevTools applies properties suitable to a development environment. These properties disable template caching, enable debug logging for the web group, and so on. As a result, we have this sensible development-time configuration without setting any properties.
- Applications using DevTools restart whenever a file on the classpath changes. This is a very helpful feature in development, as it gives quick feedback for modifications.
- By default, static resources, including view templates, don’t set off a restart. Instead, a resource change triggers a browser refresh. Notice this can only happen if the LiveReload extension is installed in the browser to interact with the embedded LiveReload server that DevTools contains.

# SpringBoot Spring Security

- Minimal configuration is needed for implementation. 
- add spring-boot-starter-security starter in the file pom.xml. 
- create a Spring config class that will override the required method while extending the `WebSecurityConfigurerAdapter` to achieve security in the application.

```java
package com.gkatzioura.security.securityendpoints.config;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
@Configuration
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http.authorizeRequests()
            .antMatchers("/welcome").permitAll()
            .anyRequest().authenticated()
            .and()
            .formLogin()
            .permitAll()
            .and()
            .logout()
            .permitAll();
    }
}
```

- default username - user
- default password - generated in console

```
spring.security.user.name=arpit
spring.security.user.password=tripathi
```

# Actuator

> Read More about [Actuator Endpoints](https://howtodoinjava.com/spring-boot/actuator-endpoints-example/)  
> Read more about [Production Ready Features](https://docs.spring.io/spring-boot/docs/current/reference/html/production-ready-features.html)  
> Read more about [SpringBoot Actuators](https://www.baeldung.com/spring-boot-actuators)  

**start springboot with cli command**  
```properties
server.port=7001
server.contextPath=/java2novice
```
Start a project jar for spring boot
```java
// to create new jar after clean
mvn clean install
// run the jar file
java -jar my-sample-application.jar --server.port=9090 --site.name=java2novice.com
```

- Actuator brings production ready features to our application without having to actually implement these features by ourselves.
- allow us to monitor and manage applications when they’re running in production.
- Exposes info about running application - health, metrics, info, logs, env, jvm etc.
- Uses http endpoints or JMX beans to enable us to interact with it.
- http endpoints : /actuator/{identityOfEndpoint}
- It helps in checking the current state of an application within the production environment. With the help of actuators, it is always easy monitoring matrices and checking your application.

```java
// gradle depedency
dependencies { compile("org.springframework.boot:spring-boot-starter-actuator") }

// pom dependency
<dependency>
 <groupId>org.springframework.boot</groupId> 
<artifactId>spring-boot-starter-actuator</artifactId> 
</dependency>
```
```properties
management.endpoints.enabled-by-default=false 
management.endpoint.info.enabled=true
management.endpoints.jmx.exposure.include=health,info
management.endpoints.web.exposure.include=* 
management.endpoints.web.exposure.exclude=env,beans
management.endpoints.web.exposure.include=env,info,health,httptrace,logfile,metrics,mappings
```
```properties
# Generic
management.endpoint.<id>.enabled=true
```

If you use Spring MVC or Spring WebFlux, Actuator’s web endpoints can be configured to support CORS scenarios.
```properties
management.endpoints.web.cors.allowed-origins=https://example.com 
management.endpoints.web.cors.allowed-methods=GET,POST
```

![actuator-endpoints]({{site.cdn}}/spring/spring-boot/actuator-endpoints.png)
- httptrace: Displays HTTP trace information
- mappings: Displays a list of all @RequestMapping paths

Here are a few issues that can be resolved with the Spring Cloud.
- reduces the complexity associated with distributed systems.
- able to handle service delivery.
- can solve redundancy issues too.
- helps in load balancing.
- reduces performance issues.



# SpringBoot Testing

> Read more about [E2E Testing](https://dzone.com/articles/all-you-need-to-know-about-end-to-end-testing){:target="_blank"}
> Read articles related to [integration tests](https://www.baeldung.com/integration-testing-in-spring){:target="_blank"} and [unit tests in JUnit 5]( https://www.baeldung.com/junit-5){:target="_blank"}.

End-to-end testing validates all the processes in the workflow to check if everything is working as expected. It also ensures that the system works in a unified manner, thereby satisfying the business requirement.

## Integration Test

When running integration tests for a Spring application, we must have an ***ApplicationContext***.

- **@SpringBootTest** : creates an ApplicationContext from configuration classes indicated by its classes attribute.
-	***In case the classes attribute isn’t set, Spring Boot searches for the primary configuration class***. The search starts from the package containing the test up until it finds a class annotated with `@SpringBootApplication` or `@SpringBootConfiguration`.
- if we use JUnit 4, we must decorate the test class with `@RunWith(SpringRunner.class)`.

> Read more about [SpringBoot Testing](https://www.baeldung.com/spring-boot-testing){:target="_blank"}

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
    <version>2.0.4.RELEASE</version>
</dependency>
```

The [spring-boot-starter-test]( https://search.maven.org/classic/#search%7Cgav%7C1%7Cg%3A%22org.springframework.boot%22%20AND%20a%3A%22spring-boot-starter-test%22){:target="_blank"} is the primary dependency that contains the majority of elements required for our tests.

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
        Employee alex = new Employee("alex");
        entityManager.persist(alex);
        entityManager.flush();
        Employee found = employeeRepository.findByName(alex.getName());
        assertEquals(found.getName(), alex.getName());
    }
}
```

**@RunWith(SpringRunner.class)** is used to provide a bridge between Spring Boot test features and JUnit. Whenever we are using any Spring Boot testing features in out JUnit tests, this annotation will be required.

-	To carry out some DB operation, we need some records already setup in our database. To setup such data, we can use `TestEntityManager`. 
-	***TestEntityManager provided by Spring Boot is an alternative to the standard JPA EntityManager that provides methods commonly used when writing tests***.

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
        Mockito.when(employeeRepository.findByName(alex.getName())).thenReturn(alex);
    }
    
    @Test
    public void whenValidName_thenEmployeeShouldBeFound() {
        String name = "alex";
        Employee found = employeeService.getEmployeeByName(name);
        assertThat(found.getName()).isEqualTo(name);
    }
}
```
- To check the Service class, we need to have an instance of Service class created and available as a @Bean so that we can @Autowire it in our test class. This configuration is achieved by using the `@TestConfiguration` annotation.
- During component scanning, we might find components or configurations created only for specific tests accidentally get picked up everywhere. To help prevent that, ***Spring Boot provides @TestConfiguration annotation that can be used on classes in src/test/java to indicate that they should not be picked up by scanning***.
- Another interesting thing here is the use of @MockBean. It creates a Mock for the EmployeeRepository which can be used to bypass the call to the actual EmployeeRepository.

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
    	List<Employee> allEmployees = Arrays.asList(alex);
    	when(service.getAllEmployees()).thenReturn(allEmployees);
    	mvc.perform(get("/api/employees")
      	    .contentType(MediaType.APPLICATION_JSON))
      	    .andExpect(status().isOk())
      	    .andExpect(jsonPath("$", hasSize(1)))
      	    .andExpect(jsonPath("$[0].name", is(alex.getName())));
    }
}
```

-	To test the Controllers, we can use @WebMvcTest. It will auto-configure the Spring MVC infrastructure for our unit tests.
-	In most of the cases, @WebMvcTest will be limited to bootstrap a single controller. It is used along with @MockBean to provide mock implementations for required dependencies.
-	@WebMvcTest also auto-configures MockMvc which offers a powerful way of easy testing MVC controllers without starting a full HTTP server.

## Integration Testing with @SpringBootTest

-	**Ideally, we should keep the integration tests separated from the unit tests and should not run along with the unit tests**. We can do that by using a different profile to only run the integration tests. 
-	A couple of reasons for doing this could be that the integration tests are time-consuming and might need an actual database to execute.

```java
@RunWith(SpringRunner.class)
@SpringBootTest(  SpringBootTest.WebEnvironment.MOCK,   classes = Application.class)
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
      .andExpect(content()
      .contentTypeCompatibleWith(MediaType.APPLICATION_JSON))
      .andExpect(jsonPath("$[0].name", is("bob")));
  }
}
```

-	The `@SpringBootTest` annotation can be used when we need to bootstrap the entire container. The annotation works by creating the ApplicationContext that will be utilized in our tests.
-	We can use the `webEnvironment` attribute of @SpringBootTest to configure our runtime environment; we’re using `WebEnvironment.MOCK` here – so that the container will operate in a mock servlet environment.
-	We can use the `@TestPropertySource` annotation to configure locations of properties files specific to our tests. Please note that the property ***file loaded with @TestPropertySource will override the existing application.properties file***.
-	The difference from the Controller layer unit tests is that here nothing is mocked and end-to-end scenarios will be executed.

## Auto-Configured Tests

One of the amazing features of Spring Boot’s auto-configured annotations is that it helps to load parts of the complete application and test specific layers of the codebase.

In addition to the above-mentioned annotations here’s a list of a few widely used annotations:
- **@WebFluxTest** – to test Spring Webflux controllers. used along with @MockBean to provide mock implementations for required dependencies.
- **@JdbcTest** – to test JPA applications but it’s for tests that only require a DataSource. The annotation configures an in-memory embedded database and a JdbcTemplate.
- **@JooqTest** – to test jOOQ-related tests we can use @JooqTest annotation, which configures a DSLContext.
- **@DataMongoTest** – to test MongoDB applications @DataMongoTest is a useful annotation. By default, it configures an in-memory embedded MongoDB if the driver is available through dependencies, configures a MongoTemplate, scans for @Document classes, and configures Spring Data MongoDB repositories.
- **@DataRedisTest** – makes it easier to test Redis applications. It scans for @RedisHash classes and configures Spring Data Redis repositories by default.
- **@DataLdapTest** – configures an in-memory embedded LDAP (if available), configures a LdapTemplate, scans for @Entry classes, and configures Spring Data LDAP repositories by default
- **@RestClientTest** – we generally use the @RestClientTest annotation to test REST clients. It auto-configures different dependencies like Jackson, GSON, and Jsonb support, configures a RestTemplateBuilder, and adds support for MockRestServiceServer by default.


# Temporary

```
maven clean package ---> cleans and packages the app as jar
```
### Conditional Beans Annotation
- @ConditionalOnClass
- @ConditionalOnBean
- @ConditionalOnProperty
- @ConditionalOnMissingBean

### Preconfigured properties
- @EnableConfigurationProperties

### Configurations
- application.yaml or application.properties
- env variables
- cloud configs (config server, vault, consul)
- spring cloud

### Flex properties without any extra container
spring.profiles.active
```
Java -jar -Dspring.profiles.active=dev
```
```
spring:
 profile:dev
server:
 port:8080
---
spring:
 profile:test
server:
 port:9090
```

### TLS/SSL
```
server.ssl.key-store
server.ssl.key-store-type
server.ssl.key-alias
server.ssl.key-password
server.ssl.key-store-type:JKS
```
Template engine --> thymeleaf

### @EnableAutoConfiguration
- Allows config classes to be scanned dynamically
- @AutoConfigureBefore and @AutoConfigureAfter
- Preconfigured default properties for autoconfiguration
- @EnableConfigurationProperties specifies default classes for property set.

### Important Annotations
- @RestController
- @RequestMapping("/api")
- @GetMapping("/greeting")

# API logs vs Application Logs

# ToDo

```
server.compression.enable=true
```
- Web starter
- spring-boot-starter-web
- Jackson JSON marshal useful for RESTful web services
- Logging framework slfj4
- Snake YAML
- Default embedded tomcat server with default config
- Validators (java, hibernate)
- JMX-exposed beans shutdown
- Spring cloud
- @RestController
- @RestControllerAdvice
- Default servlet /
- ServletContextIntializer
- Property Based Tomcat
- Server address, port, contextpath
- Session based configs(cookies, timeout)
- Server error page path
- response >= 2048 bytes for compression
- text/html, xml, plain, css eligible for compression
- Live reload server (devtools)
- BeanConfiguration
- ComponentScanning
- @Configuration, @EnableAutoConfiguration and @ComponentScan
- SpringBoot
- What is springboot
- What is starter projects
- Spring mvc vs spring REST vs springBoot
- @EnableAtoConfiguration
- @SpringBootConfiguration
- @RunWith(SpringRunner.class)
- @RestController
- Disable specific auto-config
- Register custom auto-config
- @Conditional
- @conditionalOnMissing
- Deploy as jar or war
- Command-line application
- external properties file
- application.properties or application.yml
- JVM argument
- -Dspring.profiles.active=dev
- Relaxed binding
- devtools
- Actuator
- Actuator endpoints
- SpringBoot is opinionated
- https://mindmajix.com/microservices-interview-questions
- https://dzone.com/articles/microservices-externalized-configuration
- @PropertySource


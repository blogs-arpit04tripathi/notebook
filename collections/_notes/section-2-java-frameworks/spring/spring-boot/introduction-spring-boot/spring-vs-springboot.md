---
layout: post
title: Spring vs SpringBoot
permalink: /:collection/spring/boot/spring-vs-springboot
---

- TOC
{:toc}

<hr><br>


# 1. Dependencies - SpringBoot needs 'spring-boot-starter-web'

| Spring 	| SpringBoot 	|
|---------|-------------|
| - Spring JDBC<br>- Spring MVC<br>- Spring Security<br>- Spring AOP<br>- Spring ORM<br>- Spring Test 	| - spring-boot-starter-data-jpa<br>- spring-boot-starter-security<br>- spring-boot-starter-test<br>- spring-boot-starter-web<br>- spring-boot-starter-thymeleaf <br>	|

**Spring**
```xml
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-web</artifactId>
    <version>5.1.0.RELEASE</version>
</dependency>
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-webmvc</artifactId>
    <version>5.1.0.RELEASE</version>
</dependency>
```
**SpringBoot** 
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
    <version>2.0.5.RELEASE</version>
</dependency>
```

# 2. MVC Configuration - SpringBoot gives AutoConfiguration and application.properties

**Spring requires defining the dispatcher servlet, mappings, and other supporting configurations.**

This can done either with `web.xml` file or an `Initializer class`:
```java
public class MyWebAppInitializer implements WebApplicationInitializer {
    @Override
    public void onStartup(ServletContext container) {
      AnnotationConfigWebApplicationContext context = new AnnotationConfigWebApplicationContext();
      context.setConfigLocation("com.baeldung");
      container.addListener(new ContextLoaderListener(context));
      ServletRegistration.Dynamic dispatcher = container.addServlet("dispatcher", new DispatcherServlet(context));
      dispatcher.setLoadOnStartup(1);
      dispatcher.addMapping("/");
    }
}
```
We also need to add the `@EnableWebMvc` annotation to a `@Configuration` class and define a view-resolver for views returned from the controllers:
```java
@EnableWebMvc
@Configuration
public class ClientWebConfig implements WebMvcConfigurer { 
   @Bean
   public ViewResolver viewResolver() {
      InternalResourceViewResolver bean = new InternalResourceViewResolver();
      bean.setViewClass(JstlView.class);
      bean.setPrefix("/WEB-INF/view/");
      bean.setSuffix(".jsp");
      return bean;
   }
}
```
Spring Boot only needs a couple of properties to make things work, once we’ve added the web starter:
```properties
spring.mvc.view.prefix=/WEB-INF/jsp/
spring.mvc.view.suffix=.jsp
```
**All the Spring configuration above is automatically included by adding the Boot web starter, through a process called auto-configuration.**

What this means is that Spring Boot will look at the dependencies, properties, and beans that exist in the application and enable configuration based on these.

# 3. Spring Security Configuration - SpringBoot needs only 'spring-boot-starter-security'

- Spring requires below 2 dependencies to set up Security in an application.
    - **spring-security-web**
    - **spring-security-config**
- Next, we need to add a class that extends the `WebSecurityConfigurerAdapter` and makes use of the `@EnableWebSecurity` annotation:

```java
@Configuration
@EnableWebSecurity
public class CustomWebSecurityConfigurerAdapter extends WebSecurityConfigurerAdapter {

    @Autowired
    public void configureGlobal(AuthenticationManagerBuilder auth) throws Exception {
        auth.inMemoryAuthentication().withUser("user1").password(passwordEncoder()
            .encode("user1Pass")).authorities("ROLE_USER");
    }
  
    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http.authorizeRequests().anyRequest().authenticated().and().httpBasic();
    }
     
    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }
}
```
Similarly, Spring Boot also requires these dependencies to make it work. But we *need to define only the dependency of spring-boot-starter-security as this will automatically add all the relevant dependencies to the classpath.*
*The security configuration in Spring Boot is the same as the one above.*

If you need to know how the JPA configuration can be achieved in both Spring and Spring Boot, then check out our article [A Guide to JPA with Spring](https://www.baeldung.com/the-persistence-layer-with-spring-and-jpa){:target="_blank"}.

# 4. Application Bootstrap - SpringBoot with '@SpringBootApplication'

The basic difference in bootstrapping of an application in Spring and Spring Boot lies with the servlet. Spring uses either the web.xml or **SpringServletContainerInitializer** as its bootstrap entry point.
On the other hand, Spring Boot uses only Servlet 3 features to bootstrap an application. Let’ talk about this in detail.

## How Spring Bootstraps?
Spring supports both the legacy web.xml way of bootstrapping as well as the latest Servlet 3+ method.

Let’s see the web.xml approach in steps:
- Servlet container (the server) reads web.xml
- The DispatcherServlet defined in the web.xml is instantiated by the container
- DispatcherServlet creates WebApplicationContext by reading WEB-INF/{servletName}-servlet.xml
- Finally, the DispatcherServlet registers the beans defined in the application context

Here’s how Spring bootstraps using Servlet 3+ approach:
- The container searches for classes implementing ServletContainerInitializer  and executes
- The SpringServletContainerInitializer finds all classes implementing WebApplicationInitializer
- The WebApplicationInitializer creates the context with XML or @Configuration classes
- The WebApplicationInitializer creates the DispatcherServlet with the previously created context.

## How Spring Boot Bootstraps?
The entry point of a Spring Boot application is the class which is annotated with **@SpringBootApplication**:
```java
@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```
- By default, Spring Boot uses an embedded container to run the application. 
- In this case, Spring Boot uses the public static void main entry-point to launch an embedded web server.
- Also, it takes care of the binding of the Servlet, Filter, and ServletContextInitializer beans from the application context to the embedded servlet container.
- Another feature of Spring Boot is that it automatically scans all the classes in the same package or sub packages of Main-class for components.

Spring Boot provides the option of deploying it as a web archive in an external container as well. In this case, we have to extend the *SpringBootServletInitializer*:
```java
@SpringBootApplication
public class Application extends SpringBootServletInitializer {
    // ...
}
```
Here the external servlet container looks for the Main-class defined in the META-INF file of the web archive and the **SpringBootServletInitializer** will take care of binding the Servlet, Filter, and ServletContextInitializer.

# 5. Packaging and Deployment

- Both of these frameworks support the common package managing technologies like Maven and Gradle. But when it comes to deployment, these frameworks differ a lot.
- For instance, the *Spring Boot Maven Plugin* provides Spring Boot support in Maven. It also allows packaging executable jar or war archives and running an application “in-place”.
- Some of the advantages of Spring Boot over Spring in the context of deployment include:
    - Provides embedded container support
    - Provision to run the jars independently using the command `java -jar`
    - Option to exclude dependencies to avoid potential jar conflicts when deploying in an external container
    - Option to specify active profiles when deploying
    - Random port generation for integration tests
- maven clean package: cleans the project directory and packages as jar
- Packaged jar has `code + tomcat`, application code and server.
- command line to run
  - `java -jar`
  - `mvn spring-boot:run`, spring boot maven plugin
- Spring Boot maven plugin
  - mvnw allows you to run maven project
    - no need to have maven installed or present on your path
    - if correct maven version not found, automatically downloads correct version and runs maven
  - Two files are provided
    - mvnw .cmd for MS Windows
    - mvnw .sh for Linux/Mac
    - `mvnw spring-boot:run`

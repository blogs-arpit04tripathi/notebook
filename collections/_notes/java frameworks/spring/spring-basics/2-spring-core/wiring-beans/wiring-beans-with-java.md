---
layout: post
title: Wiring Beans with Java
permalink: /:collection/spring/wiring-beans-with-java
---

- When need to wire components from some third-party library where you cannot annotate its classes with @Component and @Autowired. Then you must turn to explicit configuration (Java or XML). 
- JavaConfig is preferred for explicit configuration - more powerful, type-safe, and refactor-friendly.
- JavaConfig is often set apart in a separate package from the rest of an application’s.

# Create a Configuration Class
- **@Configuration**
  - Identifies as a configuration class.
  - It’s expected to contain details on beans that are to be created in the Spring application context.
- **@Bean** 
  - Tells Spring that returned object should be registered as a bean in the Spring application context.
  - By default, the bean will be given an ID that is the same as the @Bean-annotated method’s name.
  - By default, all beans in Spring are singletons, Spring will intercept any calls to @Bean method to return same instance again.

```java
public class Foo {
    public void init() { /* initialization logic */ }
}

public class Bar {
    public void cleanup() { /* destruction logic */ }
}

// Creating Bean using @Bean attributes
@Configuration
public class AppConfig {
    @Bean(initMethodName="init")
    public Foo foo() { return new Foo();}

    @Bean(destroyMethodName="cleanup")
    public Bar bar() {return new Bar();}
}
```


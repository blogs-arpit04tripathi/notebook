---
layout: post
title: Annotation - @Bean 
permalink: /:collection/spring/annotation/bean
---

- method-level annotation, analogous of the XML <bean/> element.
- Spring's [lifecycle Callbacks](https://docs.spring.io/spring/docs/2.5.x/reference/beans.html#beans-factory-nature) are fully supported.
- If a bean implements InitializingBean, DisposableBean, or Lifecycle, their respective methods will be called by the container.

```java
@Configuration
public class AppConfig {
    @Bean
    public TransferService transferService() {
        return new TransferServiceImpl();
    }
}
```
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

# @Bean Attributes
- [init-method](https://docs.spring.io/spring/docs/2.5.x/reference/beans.html#beans-factory-lifecycle-initializingbean){:target="_blank"}
- [destroy-method](https://docs.spring.io/spring/docs/2.5.x/reference/beans.html#beans-factory-lifecycle-disposablebean){:target="_blank"}
- [autowiring](https://docs.spring.io/spring/docs/2.5.x/reference/beans.html#beans-factory-autowire){:target="_blank"}
- [lazy-init](https://docs.spring.io/spring/docs/2.5.x/reference/beans.html#beans-factory-lazy-init){:target="_blank"}
- [dependency-check](https://docs.spring.io/spring/docs/2.5.x/reference/beans.html#beans-factory-dependencies){:target="_blank"}
- [depends-on](https://docs.spring.io/spring/docs/2.5.x/reference/beans.html#beans-factory-dependson){:target="_blank"}
- [scope](https://docs.spring.io/spring/docs/2.5.x/reference/beans.html#beans-factory-scopes){:target="_blank"}

# Supported Interfaces
- [BeanFactoryAware](https://docs.spring.io/spring/docs/2.5.x/reference/beans.html#beans-factory-aware-beanfactoryaware){:target="_blank"}
- [BeanNameAware](https://docs.spring.io/spring/docs/2.5.x/reference/beans.html#beans-factory-aware-beannameaware){:target="_blank"} - SetBeanName
- [MessageSourceAware](https://docs.spring.io/spring/docs/2.5.x/reference/beans.html#context-functionality-messagesource){:target="_blank"}
- [ApplicationContextAware](https://docs.spring.io/spring/docs/2.5.x/reference/beans.html#context-functionality-events){:target="_blank"} - setApplicationContext
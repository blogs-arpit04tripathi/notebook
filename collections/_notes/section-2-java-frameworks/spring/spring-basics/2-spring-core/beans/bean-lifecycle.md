---
layout: post
title: Lifecycle of Bean
permalink: /:collection/spring/bean-lifecycle
---


![]({{site.cdn}}/spring/spring-core/bean-lifecycle.png)

-	Spring ***instantiates*** the bean.
-	Spring injects values and bean references into the ***bean’s properties***.
-	BeanNameAware, Spring passes the bean’s ID to the ***setBeanName()*** method.
-	BeanFactoryAware, Spring calls the ***setBeanFactory()***, passing in the bean factory itself.
-	ApplicationContextAware, Spring calls the ***setApplicationContext()***, passing in a reference to the enclosing application context.
-	*BeanPostProcessor*, Spring calls its ***postProcessBeforeInitialization()*** method.
-	InitializingBean, Spring calls its ***afterPropertiesSet()*** method. 
-	***init()*** method of bean, specified initialization method is called.
-	*BeanPostProcessor*, Spring calls ***postProcessAfterInitialization()***.
-	At this point, the bean is ***ready to be used*** by the application and remains in the application context until the application context is destroyed.
-	DisposableBean, Spring calls ***destroy()***.
-	If the bean was declared with a ***custom destroy-method***, the specified method is called.

But an empty container isn’t much good by itself; it doesn’t contain anything unless you put something in it.  
To achieve the benefits of Spring DI, you must wire your application objects into the Spring container.
```xml
<beans>
   <bean id = "beanTeamplate" abstract = "true">
      <property name = "message1" value = "Hello World!"/>
      <property name = "message2" value = "Hello Second World!"/>
   </bean>
   <bean id = "helloIndia" class = "com.tutorialspoint.HelloIndia" parent = "beanTeamplate">
      <property name = "message1" value = "Hello India!"/>
   </bean>   
</beans>
```

***lifecycle of a prototype bean***
- In contrast to the other scopes, Spring does not manage the complete lifecycle of a prototype bean.
- The container instantiates, configures, and otherwise assembles a prototype object, and hands it to the client, with no further record of that prototype instance.
- Thus, although initialization lifecycle callback methods are called on all objects regardless of scope, in the case of prototypes, configured destruction lifecycle callbacks are not called.
  - The client code must clean up prototype-scoped objects and release expensive resources that the prototype bean(s) are holding.
- Solution - implement the DisposableBean interface and provides the destroy() method.
  - `@PostConstruct` and `@PreDestroy`
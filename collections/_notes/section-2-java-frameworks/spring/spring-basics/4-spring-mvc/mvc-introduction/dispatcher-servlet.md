---
layout: post
title: DispatcherServlet
permalink: /:collection/spring/mvc/dispatcher-servlet
---

- ***DispatcherServlet***
  - implementation of FrontController.
  - Java Servlet component.
  - receives all incoming HTTP request. 
  - is a HttpServlet. 
- configured in web application deployment descriptor(web.xml)
  - can configure initialization parameters to alter the behavior of DispatcherServlet.
- Servlet container
  - classpath classes which implement **ServletContainerInitializer** interface. 
  - implementation by spring, **ServletContainerInitializer --> SpringServletContainerInitializer**.
    - It seeks out implementation of **WebApplicationInitializer** and delegates to them for configuration. 
  - implementation by spring, **WebApplicationInitializer -> AbstractAnnotationConfigDispatcherServletInitializer**.
  - Any class that extends **AbstractAnnotationConfigDispatcherServletInitializer** will automatically be used to configure DispatcherServlet and the Spring application context in the application’s servlet context.

```java
public class SpittrWebAppInitializer extends AbstractAnnotationConfigDispatcherServletInitializer {

 @Override
 protected String[] getServletMappings() { 
   return new String[] { "/" };
   // paths that DispatcherServlet will be mapped to.
   // "/" means application’s default servlet ie. handle all requests
 }

 @Override
 protected Class<?>[] getRootConfigClasses() {   
   return new Class<?>[] { RootConfig.class };
   // application context
 }

 @Override
 protected Class<?>[] getServletConfigClasses() {
   return new Class<?>[] { WebConfig.class };
   // servlet context
 }
}
```

- Configuring DispatcherServlet via `AbstractAnnotationConfigDispatcherServletInitializer` is an alternative to the traditional web.xml file.
- **AbstractAnnotationConfigDispatcherServletInitializer** creates both a DispatcherServlet and a ContextLoaderListener.
- **ContextLoaderListener**
  - Spring application context.
  - @Configuration class returned getRootConfigClasses() will be used to configure the application context created by ContextLoaderListener.
    - Here, RootConfig configuration class.
  - load beans for middle-tier and data-tier components.
- **DispatcherServlet**
  - load beans containing web components such as controllers, view resolvers, and handler mappings.
  - The @Configuration classes returned from getServletConfigClasses() will define beans for DispatcherServlet’s application context.
    - Here, WebConfig configuration class.

```xml
<listener>
 	<listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
</listener>
<context-param>
  	<param-name>contextConfigLocation</param-name>
   	<param-value>/WEB-INF/root-context.xml</param-value>
</context-param>
<servlet>
 	<servlet-name>dispatcher</servlet-name>
 	<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
 	<init-param>
   		<param-name>contextConfigLocation</param-name>
   		<param-value>classpath:/context/dispatcher-servlet.xml</param-value>
 	</init-param>
 	<load-on-startup>1</load-on-startup>
</servlet>
<servlet-mapping>
  	<servlet-name>dispatcher</servlet-name>
  	<url-pattern>/</url-pattern>
</servlet-mapping>
```

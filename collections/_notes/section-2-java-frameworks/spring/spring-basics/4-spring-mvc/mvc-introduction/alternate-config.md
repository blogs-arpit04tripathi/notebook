---
layout: post
title: Alternate Spring MVC configuration
permalink: /:collection/spring/mvc/alternate-config
---

- TOC
{:toc}

<hr><br>

- setting up Spring MVC by extending `AbstractAnnotationConfigDispatcherServletInitializer`.
  - assumes that we want a basic `DispatcherServlet` and `ContextLoaderListener` setup.
  - assumes configuration will be in Java instead of XML. 
- you may need to configure DispatcherServlet in a traditional web.xml file.

# Customizing DispatcherServlet configuration

- `customizeRegistration()`
  - called after AbstractAnnotationConfigDispatcherServletInitializer registers DispatcherServlet with the servlet container.
    - param `ServletRegistration.Dynamic`
  - By overriding customizeRegistration(), you can apply additional configuration to DispatcherServlet.
  - setLoadOnStartup() - set the load-on-startup priority
  - setInitParameter() - set an initialization parameter
  - setMultipartConfig() - configure Servlet 3.0 multipart support
    - example - multipart support to temporarily store uploaded files at /tmp/spittr/uploads.

```java
@Override
protected void customizeRegistration(Dynamic registration) {
   registration.setMultipartConfig(new MultipartConfigElement("/tmp/spittr/uploads"));
}
```

# Adding additional servlets and filters

Given the way that AbstractAnnotationConfigDispatcherServletInitializer is defined, it will create a DispatcherServlet and a ContextLoaderListener. But what if you want to register additional servlets, filters, or listeners?

One of the nice things about working with a Java-based initializer is that (unlike with web.xml) you can define as many initializer classes as you want. Therefore, if you need to register any additional components into the web container, you need only create a new initializer class. The easiest way to do this is by implementing Spring’s WebApplicationInitializer interface.

```java
public class MyServletInitializer implements WebApplicationInitializer {
    @Override
    public void onStartup(ServletContext servletContext) throws ServletException {
        Dynamic myServlet = servletContext.addServlet("myServlet", MyServlet.class);
        myServlet.addMapping("/custom/**");
    }
}

@Override
public void onStartup(ServletContext servletContext)
throws ServletException {
    javax.servlet.FilterRegistration.Dynamic filter = servletContext.addFilter("myFilter", MyFilter.class);
    filter.addMappingForUrlPatterns(null, false, "/custom/*");
}
```
To register one or more filters and map them to DispatcherServlet, all you need to do is override the getServletFilters() method of AbstractAnnotationConfigDispatcherServletInitializer.
```java
@Override
protected Filter[] getServletFilters(){ return new Filter[] { new MyFilter() }; }
```
This method returns an array of javax.servlet.Filter. Here it only returns a single filter, but it could return as many filters as you need. There’s no need to declare the mapping for the filters; any filter returned from getServletFilters() will automatically be mapped to DispatcherServlet.

# Declaring DispatcherServlet in web.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://java.sun.com/xml/ns/javaee"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" version="2.5"
        xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd">
   <context-param>
      <param-name>contextConfigLocation</param-name>
      <param-value>/WEB-INF/spring/root-context.xml</param-value>
   </context-param>
   <listener>
      <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
   </listener>
   <servlet>
      <servlet-name>appServlet</servlet-name>
      <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
      <load-on-startup>1</load-on-startup>
   </servlet>
   <servlet-mapping>
      <servlet-name>appServlet</servlet-name>
      <url-pattern>/</url-pattern>
   </servlet-mapping>
</web-app>
```
`ContextLoaderListener` and `DispatcherServlet` each load a Spring application context. The contextConfigLocation context parameter specifies the location of the XML file that defines the root application context loaded by ContextLoaderListener. As defined in listing 7.3, the root context is loaded with bean definitions in /WEB-INF/spring/root-context.xml. DispatcherServlet loads its application context with beans defined in a file whose name is based on the servlet name. In listing 7.3, the servlet is named appServlet. Therefore, DispatcherServlet loads its application context from an XML file at /WEB-INF/appServlet-context.xml.

If you’d rather specify the location of the DispatcherServlet configuration file, you can set a contextConfigLocation initialization parameter on the servlet. For example, the following DispatcherServlet configuration has DispatcherServlet loading its beans from /WEB-INF/spring /appServlet/servlet-context.xml:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<servlet>
   <servlet-name>appServlet</servlet-name>
   <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
   <init-param>
      <param-name>contextConfigLocation</param-name>
      <param-value>/WEB-INF/spring/appServlet/servlet-context.xml</param-value>
   </init-param>
   <load-on-startup>1</load-on-startup>
</servlet>
```

- To use Java-based configuration in Spring MVC
  - you need to tell DispatcherServlet and ContextLoaderListener to use AnnotationConfigWebApplicationContext, an implementation of WebApplicationContext that loads Java configuration classes instead of XML.
- You can do that by setting
  - context parameter - `contextClass` 
  - initialization parameter for DispatcherServlet.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://java.sun.com/xml/ns/javaee"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" version="2.5"
        xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd">
   <context-param>
      <param-name>contextClass</param-name>
      <param-value>org.springframework.web.context.support.AnnotationConfigWebApplicationContext</param-value>
   </context-param>
   <context-param>
      <param-name>contextConfigLocation</param-name>
      <param-value>com.habuma.spitter.config.RootConfig</param-value>
   </context-param>
   <listener>
      <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
   </listener>
   <servlet>
      <servlet-name>appServlet</servlet-name>
      <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
      <init-param>
         <param-name>contextClass</param-name>
         <param-value>org.springframework.web.context.support.AnnotationConfigWebApplicationContext</param-value>
      </init-param>
      <init-param>
         <param-name>contextConfigLocation</param-name>
         <param-value>com.habuma.spitter.config.WebConfig</param-value>
      </init-param>
      <load-on-startup>1</load-on-startup>
   </servlet>
   <servlet-mapping>
      <servlet-name>appServlet</servlet-name>
      <url-pattern>/</url-pattern>
   </servlet-mapping>
</web-app>
```

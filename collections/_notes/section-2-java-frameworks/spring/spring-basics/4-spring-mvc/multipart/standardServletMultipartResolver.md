---
layout: post
title: StandardServletMultipartResolver
permalink: /:collection/spring/mvc/multipart/StandardServletMultipartResolver
---

# Resolving Multipart Requests With Servlet 3.0

- It’s possible to configure constraints on StandardServletMultipartResolver.
- you must specify multipart configuration in the servlet configuration rather than Spring configuration.
  - More specifically, you must configure multipart details as part of DispatcherServlet’s configuration in web.xml or in the servlet initializer class.
- StandardServletMultipartResolver has no constructor arguments or properties to be set.
- StandardServletMultipartResolver won’t work unless you configure this minimum detail.
  - you must specify the temporary file path where the file will be written during the upload.
- override the customizeRegistration() method of class that extends AbstractAnnotationConfigDispatcherServletInitializer or AbstractDispatcherServletInitializer.

```java
@Bean
public MultipartResolver multipartResolver() throws IOException {
  return new StandardServletMultipartResolver();
}
```

```java
DispatcherServlet ds = new DispatcherServlet();
Dynamic registration = context.addServlet("appServlet", ds);
registration.addMapping("/");
registration.setMultipartConfig(new MultipartConfigElement("/tmp/spittr/uploads"));
```

```java
@Override
protected void customizeRegistration(Dynamic registration) {
    registration.setMultipartConfig(new MultipartConfigElement("/tmp/spittr/uploads"));
}
```
```java
@Override
protected void customizeRegistration(Dynamic registration) {
    registration.setMultipartConfig(new MultipartConfigElement("/tmp/spittr/uploads", 2097152, 4194304, 0));
    // 2097152 - limit files to no more than 2 MB
    // 4194304 - limit the entire request to no more than 4 MB
    // to write all files to disk
}
```

The other constructor accepts the following:
-	The maximum size (in bytes) of any file uploaded. By default there is no limit.
-	The maximum size (in bytes) of the entire multipart request, regardless of how many parts or how big any of the parts are. By default there is no limit.
-	The maximum size (in bytes) of a file that can be uploaded without being written to the temporary location.
  - The default is 0, meaning that all uploaded files will be written to disk.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<servlet>
   <servlet-name>appServlet</servlet-name>
   <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
   <load-on-startup>1</load-on-startup>
   <multipart-config>
      <location>/tmp/spittr/uploads</location>
      <max-file-size>2097152</max-file-size>
      <max-request-size>4194304</max-request-size>
   </multipart-config>
</servlet>
```

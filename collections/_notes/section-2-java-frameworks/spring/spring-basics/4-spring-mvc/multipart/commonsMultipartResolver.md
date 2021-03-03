---
layout: post
title: CommonsMultipartResolver
permalink: /:collection/spring/mvc/multipart/CommonsMultipartResolver
---

# Configuring a Jakarta Commons FileUpload Multipart Resolver

- Spring offers `CommonsMultipartResolver` as an out-of-the-box alternative to `StandardServletMultipartResolver`.
- no need to configure a temporary file location with CommonsMultipartResolver.
  -  By default, the location is the servlet container’s temporary directory.
- there’s no way to specify the maximum multipart request size.

```java
@Bean
public MultipartResolver multipartResolver() {
  return new CommonsMultipartResolver();
}
```
```java
@Bean
public MultipartResolver multipartResolver() throws IOException {
  CommonsMultipartResolver multipartResolver = new CommonsMultipartResolver();
  multipartResolver.setUploadTempDir(new FileSystemResource("/tmp/spittr/uploads"));
  multipartResolver.setMaxUploadSize(2097152);
  multipartResolver.setMaxInMemorySize(0);
  return multipartResolver;
}
```

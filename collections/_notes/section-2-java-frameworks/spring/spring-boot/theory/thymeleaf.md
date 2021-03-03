---
layout: post
title: ThymeLeaf
permalink: /:collection/spring/boot/thymeleaf
---

- Java Templating Engine
- commonly used to generate html views of web apps.
- similar to jsp, but can be used outside web apps as well.
- non web usecase - email template, csv template, pdf template.
- src/main/resources/templates
  - For webapps, thymeleaf templates are .html
  - src/main/resources/static for css files

```xml
<dependency>
    <groupId>org.springframework.boot</groupId> 
    <artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>
```
```html
<!DOCTYPE HTML>
<html xmlns:th="http://www.themeleaf.org">
<head>
    <title>App Heading</title>
    <link rel="stylesheet" th:href="@{/css/demo.css}">
</head>
<body>
    <a href="xyz" onclick="if(!(confirm('Are you sure, you want to exit?'))) return false">
    </a>
</body>
```

Spring boot searches following directories for static resources
- /META-INF/resources
- /resources
- /static
- /public

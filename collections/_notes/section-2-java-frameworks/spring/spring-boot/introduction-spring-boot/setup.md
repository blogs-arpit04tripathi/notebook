---
layout: post
title: Spring Boot application Setup with Maven
permalink: /:collection/spring/boot/setup
---

- Inherit from the spring-boot-starter-parent project and declare dependencies to Spring Boot starters. 
- Doing this lets our project reuse the default settings of Spring Boot.
- To inheriting spring-boot-starter-parent, specify a parent element in pom.xml:

```xml
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.1.1.RELEASE</version>
</parent>
```
- We can find the latest version of spring-boot-starter-parent on Maven Central.
- version of `spring-boot-starter-parent` defines the version of dependencies.

***Using the starter parent project is convenient, but not always feasible.***

For instance, if our company requires all projects to inherit from a standard POM, we cannot rely on the Spring Boot starter parent.

In this case, we can still get the benefits of dependency management with this POM element:
```xml
<dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-dependencies</artifactId>
            <version>2.1.1.RELEASE</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```

---
layout: post
title: Sample pom xml with starter template
permalink: /:collection/spring/boot/starter-template/example
---

- parent pom declarations allows us to manage following things for multiple child projects.
    - Configuration
        - maintain consistency in java version and other related properties accross all sub projects.
    - Depedency Management
        - control all versions of the dependencies to avoid dependency version conflicts.
        - All versions are resolved in relation to version of parent starter.
        - inherits dependency management from spring-boot-dependencies.
    - Default Plugin Configuration
- Each starter plays a role as a one-stop shop for all the Spring technologies we need.
  - ***Other required dependencies are then transitively pulled in and managed in a consistent way***.
- All starters are under the `org.springframework.boot group`, and 
  - their names start with spring-boot-starter-.
  - ***This naming pattern makes it easy to find starters, especially when working with IDEs that support searching dependencies by name***.
- ***parent is just a configuration*** which tells what group of jars to be downloaded for mentioned dependency and the version of those jars based on parent version.
  - these preset list of combination of jars that work well without any issues is called **Bill of Materials**
  - Default configuration of spring boot plugin is defined in `spring-boot-maven-plugin`
    - allows command `mvn spring-boot:run`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
 xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
   <modelVersion>4.0.0</modelVersion>
   <groupId>com.java2novice.springboot</groupId>
   <artifactId>spring-boot-tutorials</artifactId>
   <version>0.0.1-SNAPSHOT</version>
   <!-- java version -->
   <properties>
      <java.version>1.8</java.version>
   </properties>
   <!-- Parent pom is mandatory to control versions of child dependencies -->
   <parent>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-parent</artifactId>
      <version>2.0.4.RELEASE</version>
      <relativePath />
   </parent>
   <dependencies>
      <!-- Spring web brings all required dependencies to build web application.(Tomcat, Spring MVC etc) -->
      <dependency>
         <groupId>org.springframework.boot</groupId>
         <artifactId>spring-boot-starter-web</artifactId>
         <!-- can omit the version here safely -->
      </dependency>
   </dependencies>
   <build>
      <plugins>
         <!-- Package as an executable jar/war -->
         <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
         </plugin>
      </plugins>
   </build>
</project>
```

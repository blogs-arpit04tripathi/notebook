---
layout: post
title: JUnit Setup
permalink: /:collection/junit/setup
---
**How to include JUnit 5 to your project ?**

```xml
<!-- pom.xml -->
<dependency>
    <groupId>org.junit.jupiter</groupId>
    <artifactId>junit-jupiter-engine</artifactId>
    <version>${junit.jupiter.version}</version>
</dependency>
<dependency>
    <groupId>org.junit.platform</groupId>
    <artifactId>junit-platform-runner</artifactId>
    <version>${junit.platform.version}</version>
    <scope>test</scope>
</dependency>
```

```gradle
// build.gradle
testRuntime("org.junit.jupiter:junit-jupiter-engine:5.0.0-M4")
testRuntime("org.junit.platform:junit-platform-runner:1.0.0-M4")
```

scope = test, means that the dependency jar will not be included in the final distributable.

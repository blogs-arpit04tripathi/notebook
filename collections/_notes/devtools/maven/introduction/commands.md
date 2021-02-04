---
layout: post
title: Maven
permalink: /:collection/maven/commands
---

- [Maven All Commands](http://tutorials.jenkov.com/maven/maven-commands.html)

```java
mvn clean install               // clean install
mvn clean install -DskipTests
mvn clean install -U            // clean install force update (snapshot dependencies)
mvn dependency:sources          // download sources
mvn dependency:resolve -Dclassifier=javadoc
mvn eclipse:eclipse
mvn dependency:tree > ../zz-mvn-tree.txt
```

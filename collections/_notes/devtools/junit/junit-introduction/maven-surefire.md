---
layout: post
title: Maven Surefire Plugin
permalink: /:collection/junit/surefire
---

- To run unit test using maven command, such as in jenkins pipeline.
- Run maven build as goal test.

```xml
<build>
    <plugins>
        <plugin>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>2.22.1</version>
        </plugin>
    </plugins>
</build>
```

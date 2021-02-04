---
layout: post
title: GroupId naming conventions
permalink: /:collection/maven/groupid-naming-convention
---

- [Maven groupId and package name in java source](https://stackoverflow.com/questions/5214075/maven-groupid-and-package-name-in-java-source)
- [Guide to naming conventions on groupId, artifactId, and version](https://maven.apache.org/guides/mini/guide-naming-conventions.html)


```java
your website domain = maven.apache.org      , commons.apache.org
your groupId should be = org.apache.maven   , org.apache.commons
// if the current project is a multiple module project, it should append a new identifier to the parent's groupId.
org.apache.maven, org.apache.maven.plugins, org.apache.maven.reporting
```
> `.com` is primarily used by for-profit businesses, while `.org` is largely used by nonprofit websites.

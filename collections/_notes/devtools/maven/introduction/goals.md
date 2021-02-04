---
layout: post
title: Maven Goals
permalink: /:collection/maven/goals
---

- Maven’s primary goal is to allow a developer to comprehend the complete state of a development effort in the shortest period of time. 
- In order to attain this goal there are several areas of concern that Maven attempts to deal with:
	- Making the build process easy
	- Providing a uniform build system
	- Providing quality project information
	- Providing guidelines for best practices development
    - Allowing transparent migration to new features
- [Maven Goals and Phases](https://stackoverflow.com/questions/16205778/what-are-maven-goals-and-phases-and-what-is-their-difference#:~:targetText=If%20you%20specify%20a%20goal,will%20run%20the%20jar%20goal.)

* Maven addresses two aspects of building software: first, it describes how software is built, and second, it describes its dependencies.
* Contrary to preceding tools like Apache Ant, it uses conventions for the build procedure, and only exceptions need to be written down. 
* An XML file describes the software project being built, its dependencies on other external modules and components, the build order, directories, and required plug-ins. 
* It comes with pre-defined targets for performing certain well-defined tasks such as compilation of code and its packaging.
* Maven dynamically downloads Java libraries and Maven plug-ins from one or more repositories such as the Maven 2 Central Repository, and stores them in a local cache. This local cache of downloaded artifacts can also be updated with artifacts created by local projects. Public repositories can also be updated.
* Maven allows a project to build using its **project object model (POM)** and a set of plugins that are shared by all projects using Maven, providing a uniform build system. Once you familiarize yourself with how one Maven project builds you automatically know how all Maven projects build saving you immense amounts of time when trying to navigate many projects.

Maven projects are configured using a [Project Object Model](https://en.wikipedia.org/wiki/Apache_Maven#Project_Object_Model), which is stored in a pom.xml-file.

```xml
<project>
    <!-- model version is always 4.0.0 for Maven 2.x POMs -->
    <modelVersion>4.0.0</modelVersion>
    <!-- project coordinates, i.e. a group of values which uniquely identify this project -->
    <groupId>com.mycompany.app</groupId>
    <artifactId>my-app</artifactId>
    <version>1.0</version>
    <!-- library dependencies -->
    <dependencies>
        <dependency>
            <!-- coordinates of the required library -->
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>3.8.1</version>
            <!-- this dependency is only used for running and compiling tests -->
            <scope>test</scope>
        </dependency>
    </dependencies>
</project>
```

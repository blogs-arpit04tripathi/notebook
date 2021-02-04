---
layout: post
title: Setup Jenkins on Tomcat
permalink: /:collection/jenkins/setup-on-tomcat
---

Apart from being started Jenkins on Standalone server. It can also be started on tomcat.

**Why on tomcat when it can be started on Standalone server?**
- Jenkins comes with its own servlet container – jetty/winstone.
- It can be started and deployed on tomcat and other servlet container.
- Running on tomcat – All applications can be run on single server (Not necessary)
- Required – tomcat 5+ , java 1.7+

***Steps***
* Download tomcat zip file. Extract to folder. Paste Jenkins.war in Tomcat/webapps folder.
* Make all files executable – chmod +x *.sh in command prompt.
* bin folder - ./startup.sh
* Verify if tomcat started – browser http://localhost:8080/jenkins

You can run Jenkins on tomcat and standalone simultaneously. Same Jenkins is used.

**Servers supported (servlet container)**
- Glassfish, JBoss, Tomcat
- IBM Websphere, Jetty, Jonas
- Weblogic etc.

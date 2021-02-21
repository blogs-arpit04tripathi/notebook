---
layout: post
title: Public vs Private JRE
permalink: /:collection/java/public-vs-private-jre
---

**JRE** environment, bunch of directories with Java-related files:
* /bin - executable programs java and javaw
* /lib - supporting files: jars, config files, property files, fonts, sounds, icons etc. 
	- most important is **rt.jar** containing "java API".

![public-vs-private-jre]({{site.cdn}}/java/core-java/public-vs-private-jre.png)

* JDK installation brings private JRE and optionally a public copy.
* **private JRE**
	- is required to run the tools included with the JDK and have no registry settings.
	- is contained entirely in a jre directory whose location is known only to the JDK. 
* **public JRE**
	- used by other Java apps, outside the JDK 
	- it is registered with the Windows registry (at HKEY_LOCAL_MACHINE\SOFTWARE\JavaSoft), 
	- can be removed using Add/Remove Programs, 
	- might be registered with browsers, 
	- might have the java.exe file copied to the Windows system directory.
	- (C:\Program Files\Java\jre1.7.0)
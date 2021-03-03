---
layout: post
title: Variables and scopes
permalink: /:collection/java/var-scopes
---

* **Variables**
	- basic unit of storage. (type+Identifier+optional initializer).
	- Have scope(visibility) and a lifetime.
* **Scope** - section of code where var is acessible. 
* **Lifetime** - time duration till var in a valid state, even if out of scope.

|variable scopes||
|---|---|
protected | when inheritance is involved.
public | accessible by any other code. 
private | accessed by other members of its class.
default | no access modifier, cannot be accessed outside of its package. 

* Now you can understand why **main( )** has always been preceded by the **public** modifier.
  * It is called by code that is outside the program—that is, by the Java run-time system.
* In most real-world classes, you will need to allow operations on data only through methods (getX and setX).
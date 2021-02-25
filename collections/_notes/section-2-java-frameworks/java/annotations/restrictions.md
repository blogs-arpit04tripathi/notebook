---
layout: post
title: Annotaions Restrictions
permalink: /:collection/java/annotations/restrictions
---

* No annotation can inherit another.
* all methods declared by an annotation must be without parameters. 
* they must return one of the following:
	- A primitive type, such as **int** or **double**
	- An object of type **String** or **Class**
	- An **enum** type
	- Another annotation type
	- An array of one of the preceding types
* Annotations cannot be generic, cannot take type parameters. 
* annotation methods cannot specify a **throws** clause.
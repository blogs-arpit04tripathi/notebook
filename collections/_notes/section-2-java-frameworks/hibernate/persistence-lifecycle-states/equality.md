---
layout: post
title: Equality
permalink: /:collection/hibernate/persistence/equality
---

-	Requesting a persistent object again **from the same Hibernate session returns the same Java instance of a class**, which means that you can compare the objects using the standard Java ‘==’ equality syntax.
-	If you request a persistent object from **more than one Hibernate session, Hibernate will provide distinct instances from each session**, and the == operator will return false if you compare these object instances.
-	So if you are comparing objects in two different sessions, you will need to implement the equals() method on your Java persistence objects, which you should do as a regular occurrence anyway. (Just don’t forget to override hashCode() along with it.)

**Bullet Points**
1.	Requesting a persistent object again from the same Hibernate session returns the "same java instance" of a class.
2.	Requesting a persistent object from the different Hibernate session returns "different java instance" of a class.
3.	As a best practice, always implement equals() and hashCode() methods in your hibernate entities; and always compare them using equals() method only.


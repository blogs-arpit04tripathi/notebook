---
layout: post
title: Database Normalization
permalink: /:collection/cs/dbms/database-normalization
---

- TOC
{:toc}

<hr><br>

# Database Normalization
* **Database Normalization** is the process of efficiently organizing data in a database. There are two reasons of the normalization process:
	- Eliminating redundant data, for example, storing the same data in more than one tables.
	- Ensuring data dependencies make sense.
* Both of these are worthy goals as they reduce the amount of space a database consumes and ensure that data is logically stored. Normalization consists of a series of guidelines that help guide you in creating a good database structure.
* Normalization guidelines are divided into normal forms; think of form as the format or the way a database structure is laid out. The aim of normal forms is to organize the database structure so that it complies with the rules of first normal form, then second normal form, and finally third normal form.
* It's your choice to take it further and go to fourth normal form, fifth normal form, and so on, but generally speaking, third normal form is enough.
	- [First Normal Form (1NF)](https://www.tutorialspoint.com/sql/first-normal-form.htm)
	- [Second Normal Form (2NF)](https://www.tutorialspoint.com/sql/second-normal-form.htm)
	- [Third Normal Form (3NF)](https://www.tutorialspoint.com/sql/third-normal-form.htm)
    - BCNF

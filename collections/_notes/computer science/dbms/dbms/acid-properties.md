---
layout: post
title: ACID properties in DBMS
permalink: /notes/dbms/acid-properties
---

# ACID properties in DBMS

- Certain properties are followed in order to maintain consistency in a database, before and after the transaction.

|ACID Properties||
|---|---|
|**Transaction**|A unit of program that updates various data items.<br>To ensure the integrity of data during a transaction, the database system maintains the ACID properties.|
|**Atomicity**|Ensures that either all the operations of a transaction reflect in database or none. No partial transactions.<br>Example - transferring amount between accounts.|
|**Consistency**|To preserve the consistency of database, the execution of transaction should take place in isolation (that means no other transaction should run concurrently when there is a transaction already running).<br>Example - A(400) -> 100 to each B and C. Final should be 200, not 300 which happens in concurrent transaction.|
|**Isolation**|Transactions occur independently without interference.<br>For every pair of transactions, one transaction should start execution only when the other finished execution.<br>Ensures that execution of transactions concurrently will result in a state that is equivalent to a state achieved these were executed serially in some order.|
|**Durability**|On successful transaction completion, changes made should be permanent even if there is a system failure. Stored on non-volatile memory.<br>recovery-management component of database systems ensures the durability of transaction.|

![ACID properties](https://github.com/arpit04tripathi/files-cdn/raw/cdn/dbms/dbms/ACID%20Properties.jpg)
---
layout: post
title: Java Transactions API
permalink: /:collection/java/multithreading/java-transactions-api
---


- Specification that allows applications to perform distributed transactions.
- For distributed environment,  most basic operations like commit, rollback along with concurrent processing is difficult.
- Concurrency utilities rely completely on JTA to perform and support transactions, work with XA Resource.
- Possible with javax.transaction.UserTransaction API, It helps developers to manage transaction boundaries. 
	- I may have the transaction which is spread among different threads, CPU cores, machines, or even networks. But the user transaction API that I have with me will ensure that all of these transactions operating in a single unit will be managed correctly.
- Resource Manager (Drivers) should be XA compatible, which can help you make sure that this global transaction and distributed transaction process works well.
- UserTransaction available through JNDI lookup. 

![java-transactions-api]({{site.cdn}}/java/multi-threading/java-transactions-api.png)

```java
@Resource(lookup=””)
private UserTransaction userTransaction;
```

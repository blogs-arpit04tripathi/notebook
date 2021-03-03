---
layout: post
title: Store Procedure Call
permalink: /:collection/hibernate/stored-procedure-call
---

**Native SQL – createSQLQuery**
```java
Query query = session.createSQLQuery(
	"CALL GetStocks(:stockCode)")
	.addEntity(Stock.class)
	.setParameter("stockCode", "7277");
			
List result = query.list();
for(int i=0; i<result.size(); i++){
	Stock stock = (Stock)result.get(i);
	System.out.println(stock.getStockCode());
}
```

**NamedNativeQuery in annotation**
```java
@NamedNativeQueries({
	@NamedNativeQuery(
	name = "callStockStoreProcedure",
	query = "CALL GetStocks(:stockCode)",
	resultClass = Stock.class
	)
})
@Entity
@Table(name = "stock")
public class Stock implements java.io.Serializable {

Query query = session.getNamedQuery("callStockStoreProcedure")
	.setParameter("stockCode", "7277");
List result = query.list();
for(int i=0; i<result.size(); i++){
	Stock stock = (Stock)result.get(i);
	System.out.println(stock.getStockCode());
}
```

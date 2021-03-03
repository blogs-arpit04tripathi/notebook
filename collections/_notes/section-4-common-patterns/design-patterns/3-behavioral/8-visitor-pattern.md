---
layout: post
title: Visitor Pattern
permalink: /:collection/design-patterns/behavioral/visitor-pattern
---

- TOC
{:toc}

<hr><br>

-	Visitor pattern is used when we have to perform an operation on a group of similar kind of Objects. With the help of visitor pattern, we can move the operational logic from the objects to another class.

# Example-Visitor Pattern
Consider a Shopping cart where we can add different type of items (Elements), when we click on checkout button, it calculates the total amount to be paid. Now we can have the calculation logic in item classes or we can move out this logic to another class using visitor pattern.

![]({{site.cdn}}/design-patterns/behavioral-visitor.png)

```java
public interface ItemElement {public int accept(ShoppingCartVisitor visitor);}
```
```java
public class Book implements ItemElement {
 private int price;
 private String isbnNumber;
 public Book(int cost, String isbn){
  this.price=cost;
  this.isbnNumber=isbn;
 }
 public int getPrice() {
  return price;
 }
 public String getIsbnNumber() {
  return isbnNumber;
 }
 @Override
 public int accept(ShoppingCartVisitor visitor) {
  return visitor.visit(this);
 }
}
```
```java
public class Fruit implements ItemElement {	
 private int pricePerKg;
 private int weight;
 private String name;
 public Fruit(int priceKg, int wt, String nm){
  this.pricePerKg=priceKg;
  this.weight=wt;
  this.name = nm;
 }
 public int getPricePerKg() {
  return pricePerKg;
 }
 public int getWeight() {
  return weight;
 }
 public String getName(){
  return this.name;
 }
 @Override
 public int accept(ShoppingCartVisitor visitor){
  return visitor.visit(this);
 }
}
```
Notice the implementation of accept() method in concrete classes, its calling visit() method of Visitor and passing itself as argument. We have visit() method for different type of items in Visitor interface that will be implemented by concrete visitor class.

```java
public interface ShoppingCartVisitor {
	int visit(Book book);
	int visit(Fruit fruit);
}
```
```java
public class ShoppingCartVisitorImpl implements ShoppingCartVisitor {
	@Override
	public int visit(Book book) {
		int cost=0;
		//apply 5$ discount if book price is greater than 50
		if(book.getPrice() > 50){cost = book.getPrice()-5;}else cost = book.getPrice();
		System.out.println("Book ISBN::"+book.getIsbnNumber() + " cost ="+cost);
		return cost;
	}
	@Override
	public int visit(Fruit fruit) {
		int cost = fruit.getPricePerKg()*fruit.getWeight();
		System.out.println(fruit.getName() + " cost = "+cost);
		return cost;
	}
}
```

# Benefits-Visitor Pattern
The benefit of this pattern is that if the logic of operation changes, then we need to make change only in the visitor implementation rather than doing it in all the item classes. Another benefit is that adding a new item to the system is easy, it will require change only in visitor interface and implementation and existing item classes will not be affected.

# Limitations-Visitor Pattern
The drawback of visitor pattern is that we should know the return type of visit() methods at the time of designing otherwise we will have to change the interface and all of its implementations. Another drawback is that if there are too many implementations of visitor interface, it makes it hard to extend.

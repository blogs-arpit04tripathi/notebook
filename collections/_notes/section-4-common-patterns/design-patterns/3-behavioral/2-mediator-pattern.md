---
layout: post
title: Mediator Pattern
permalink: /:collection/design-patterns/behavioral/mediator-pattern
---

- Mediator design pattern is used to provide a centralized communication medium between different objects in a system. Mediator design pattern is very helpful in an enterprise application where multiple objects are interacting with each other. If the objects interact with each other directly, the system components are tightly-coupled with each other that makes maintainability cost higher and not flexible to extend easily. Mediator pattern focuses on provide a mediator between objects for communication and help in implementing lose-coupling between objects.
- Air traffic controller is a great example of mediator pattern where the airport control room works as a mediator for communication between different flights.
- Mediator works as a router between objects and it can have it’s own logic to provide way of communication.
- The system objects that communicate each other are called **Colleagues**. Usually we have an interface or abstract class that provides the contract for communication and then we have concrete implementation of mediators.

# Example - Mediator Pattern
We will try to implement a chat application where users can do group chat. Every user will be identified by it’s name and they can send and receive messages. The message sent by any user should be received by all the other users in the group.

![]({{site.cdn}}/design-patterns/behavioral-mediator.png)

```java
public interface ChatMediator {
 public void sendMessage(String msg, User user);
 void addUser(User user);
}
```

- Users can send and receive messages, so we can have User interface or abstract class.
- Notice that User has a reference to the mediator object, it’s required for the communication between different users.

```java
public abstract class User {
 protected ChatMediator mediator;
 protected String name;
 public User(ChatMediator med, String name){
  this.mediator=med;
  this.name=name;
 }
 public abstract void send(String msg);
 public abstract void receive(String msg);
}
```

Now we will create concrete mediator class, it will have a list of users in the group and provide logic for the communication between the users.

```java
public class ChatMediatorImpl implements ChatMediator {
 private List<User> users;
 public ChatMediatorImpl(){
  this.users=new ArrayList<>();
 }
 @Override
 public void addUser(User user){
  this.users.add(user);
 }
 @Override
  public void sendMessage(String msg, User user) {
  for(User u : this.users){
  //message should not be received by the user sending it
   if(u != user){u.receive(msg);}
  }
 }
}
```

Now we can create concrete User classes to be used by client system.

```java
public class UserImpl extends User {
 public UserImpl(ChatMediator med, String name) {
  super(med, name);
 }
 @Override
 public void send(String msg){
  System.out.println(this.name+": Sending Message="+msg);
  mediator.sendMessage(msg, this);
 }
 @Override
 public void receive(String msg) {
  System.out.println(this.name+": Received Message:"+msg);
 }
}
```

Notice that send() method is using mediator to send the message to the users and it has no idea how it will be handled by the mediator.

```java
public class ChatClient {
	public static void main(String[] args) {
		ChatMediator mediator = new ChatMediatorImpl();
		User user1 = new UserImpl(mediator, "Pankaj");
		User user2 = new UserImpl(mediator, "Lisa");
		User user3 = new UserImpl(mediator, "Saurabh");
		User user4 = new UserImpl(mediator, "David");
		mediator.addUser(user1);
		mediator.addUser(user2);
		mediator.addUser(user3);
		mediator.addUser(user4);		
		user1.send("Hi All");		
	}
}
```

# JDK Example-Mediator Pattern
-	java.util.Timer class scheduleXXX() methods
-	Java Concurrency Executor execute() method.
-	java.lang.reflect.Method invoke() method.

# Mediator Design Pattern Important Points
- Mediator pattern is useful when the communication logic between objects is complex, we can have a central point of communication that takes care of communication logic.
- ***Allows loose coupling by encapsulating the way disparate sets of objects interact and communicate with each other. Allows for the actions of each object set to vary independently of one another.***
- Java Message Service (JMS) uses Mediator pattern along with Observer pattern to allow applications to subscribe and publish data to other applications.
- We should not use mediator pattern just to achieve lose-coupling because if the number of mediators will grow, then it will become hard to maintain them.
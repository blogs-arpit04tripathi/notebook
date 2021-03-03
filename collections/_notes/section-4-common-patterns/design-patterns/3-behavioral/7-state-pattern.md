---
layout: post
title: State Pattern
permalink: /:collection/design-patterns/behavioral/state-pattern
---

- TOC
{:toc}

<hr><br>

- State design pattern is used when an Object change it’s behavior based on it’s internal state.
- If we have to change the behavior of an object based on it’s state, we can have a state variable in the Object and use if-else condition block to perform different actions based on the state. State pattern is used to provide a systematic and lose-coupled way to achieve this through `Context` and `State` implementations.
- State Pattern Context is the class that has a State reference to one of the concrete implementations of the State. Context forwards the request to the state object for processing.

# Example-State Pattern
Suppose we want to implement a TV Remote with a simple button to perform action. If the State is ON, it will turn on the TV and if state is OFF, it will turn off the TV.

```java
public class TVRemoteBasic {
	private String state="";	
	public void setState(String state){this.state=state;	}	
	public void doAction(){
		if(state.equalsIgnoreCase("ON")){
			System.out.println("TV is turned ON");
		}else if(state.equalsIgnoreCase("OFF")){
			System.out.println("TV is turned OFF");
		}
	}

	public static void main(String args[]){
		TVRemoteBasic remote = new TVRemoteBasic();		
		remote.setState("ON");
		remote.doAction();		
		remote.setState("OFF");
		remote.doAction();
	}
}
```
Notice that client code should know the specific values to use for setting the state of remote. Further more if number of states increase then the tight coupling between implementation and the client code will be very hard to maintain and extend. Now we will use State pattern to implement above TV Remote example.
```java
public interface State {public void doAction();}
```
In our example, we can have two states – one for turning TV on and another to turn it off. So we will create two concrete state implementations for these behaviors.
```java
public class TVStartState implements State{
 @Override
 public void doAction() {
  System.out.println("TV is turned ON");
 }
}
```
```java
public class TVStopState implements State{
 @Override
 public void doAction() {
  System.out.println("TV is turned OFF");
 }
}
```
```java
public class TVContext implements State {
	private State tvState;
	public void setState(State state) {
		this.tvState=state;
	}
	public State getState() {
		return this.tvState;
	}
	@Override
	public void doAction() {
		this.tvState.doAction();
	}
}
```
Notice that Context also implements State and keep a reference of its current state and forwards the request to the state implementation.
```java
public class TVRemote {
 public static void main(String[] args) {
  TVContext context = new TVContext();
  State tvStartState = new TVStartState();
  State tvStopState = new TVStopState();		
  context.setState(tvStartState);
  context.doAction();		
  context.setState(tvStopState);
  context.doAction();		
 }
}
```

# Benefits-State Design Pattern
The benefits of using State pattern to implement polymorphic behavior is clearly visible. The chances of error are less and it’s very easy to add more states for additional behavior. Thus making our code more robust, easily maintainable and flexible. Also State pattern helped in avoiding if-else or switch-case conditional logic in this scenario. State Pattern is very similar to Strategy Pattern, check out Strategy Pattern in Java.

---
layout: post
title: Iterator Pattern
permalink: /:collection/design-patterns/behavioral/iterator-pattern
---

- TOC
{:toc}

<hr><br>

-	It’s used to provide a standard way to traverse through a group of Objects. Iterator pattern is widely used in Java Collection Framework where Iterator interface provides methods for traversing through a collection.
-	Iterator pattern is not only about traversing through a collection, we can provide different kind of iterators based on our requirements. Iterator pattern hides the actual implementation of traversal through the collection and client programs just use iterator methods.

***Provides a way to access the elements of an aggregate object without exposing its underlying represenation. Iterator pattern is not only about traversing through a collection, we can provide different kind of iterators based on our requirements.***

Iterator design pattern hides the actual implementation of traversal through the collection and client programs just use iterator methods.

```java
public enum ChannelTypeEnum {ENGLISH, HINDI, FRENCH, ALL;}
```
```java
public class Channel {
	private double frequency;
	private ChannelTypeEnum TYPE;	
	public Channel(double freq, ChannelTypeEnum type){
		this.frequency=freq;
		this.TYPE=type;
	}
	public double getFrequency() {return frequency;}
	public ChannelTypeEnum getTYPE() {return TYPE;}
	@Override
	public String toString(){return "Frequency="+this.frequency+", Type="+this.TYPE;}	
}
```
The first part of implementation is to define the contract for our collection and iterator interfaces.
```java
public interface ChannelCollection {
	public void addChannel(Channel c);
	public void removeChannel(Channel c);
	public ChannelIterator iterator(ChannelTypeEnum type);
}
```
-	ChannelCollection interface defines the contract for our collection class implementation. Notice that there are methods to add and remove a channel but there is no method that returns the list of channels.
-	ChannelCollection has a method that returns the iterator for traversal.

```java
public interface ChannelIterator {
	public boolean hasNext();	
	public Channel next();
}
```
```java
public class ChannelCollectionImpl implements ChannelCollection {
	private List<Channel> channelsList;
	public ChannelCollectionImpl() {channelsList = new ArrayList<>();}
	public void addChannel(Channel c) {this.channelsList.add(c);}
	public void removeChannel(Channel c) {this.channelsList.remove(c);}

	@Override
	public ChannelIterator iterator(ChannelTypeEnum type) {
		return new ChannelIteratorImpl(type, this.channelsList);
	}

	private class ChannelIteratorImpl implements ChannelIterator {
		private ChannelTypeEnum type;
		private List<Channel> channels;
		private int position;
		public ChannelIteratorImpl(ChannelTypeEnum ty, List<Channel> channelsList) {
			this.type = ty;
			this.channels = channelsList;
		}
		@Override
		public boolean hasNext() {
			while (position < channels.size()) {
				Channel c = channels.get(position);
				if (c.getTYPE().equals(type) || type.equals(ChannelTypeEnum.ALL)) {
					return true;
				} else
					position++;
			}
			return false;
		}
		@Override
		public Channel next() {
			Channel c = channels.get(position);
			position++;
			return c;
		}
	}
}
```
- Notice the inner class implementation of iterator interface so that the implementation can't be used by any other collection. Same approach is followed by collection classes also and all of them have inner class implementation of Iterator interface.

```java
public class TestIteratorPattern {

	public static void main(String[] args) {
		ChannelCollection channels = populateChannels();
		ChannelIterator baseIterator = channels.iterator(ChannelTypeEnum.ALL);
		while (baseIterator.hasNext()) {
			Channel c = baseIterator.next();
			System.out.println(c.toString());
		}
		System.out.println("******");
		// Channel Type Iterator
		ChannelIterator englishIterator = channels.iterator(ChannelTypeEnum.ENGLISH);
		while (englishIterator.hasNext()) {
			Channel c = englishIterator.next();
			System.out.println(c.toString());
		}
	}

	private static ChannelCollection populateChannels() {
		ChannelCollection channels = new ChannelCollectionImpl();
		channels.addChannel(new Channel(98.5, ChannelTypeEnum.ENGLISH));
		channels.addChannel(new Channel(99.5, ChannelTypeEnum.HINDI));
		channels.addChannel(new Channel(100.5, ChannelTypeEnum.FRENCH));
		channels.addChannel(new Channel(101.5, ChannelTypeEnum.ENGLISH));
		channels.addChannel(new Channel(102.5, ChannelTypeEnum.HINDI));
		channels.addChannel(new Channel(103.5, ChannelTypeEnum.FRENCH));
		channels.addChannel(new Channel(104.5, ChannelTypeEnum.ENGLISH));
		channels.addChannel(new Channel(105.5, ChannelTypeEnum.HINDI));
		channels.addChannel(new Channel(106.5, ChannelTypeEnum.FRENCH));
		return channels;
	}
}
```

# Iterator Design Pattern Important Points
-	Iterator pattern is useful when you want to provide a standard way to iterate over a collection and hide the implementation logic from client program.
-	The logic for iteration is embedded in the collection itself and it helps client program to iterate over them easily.

# JDK Example-Iterator Pattern 
We all know that Collection framework Iterator is the best example of iterator pattern implementation but do you know that java.util.Scanner class also Implements Iterator interface. Read this post to learn about Java Scanner Class.


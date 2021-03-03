---
layout: post
title: Anonymous Inner class
permalink: /:collection/java/anonymous-inner-class
---

- Inner class without a name.
   - for which only a single object is created.
- Useful when making an instance of an object with certain “extras” such as overloading methods of a class or interface, without having to actually subclass a class.
- Application - In writing implementation classes for listener interfaces in graphics programming.

# Types of anonymous inner class
**Anonymous Inner class that extends a class**
```java
class MyThread { 
	public static void main(String[] args){ 
		Thread t = new Thread(){ 
			public void run() { 
				System.out.println("Child Thread"); 
			} 
		}; 
		t.start(); 
		System.out.println("Main Thread"); 
	}
} 
```

**Anonymous Inner class that implements a interface**
```java
class MyThread { 
	public static void main(String[] args){ 
		Runnable r = new Runnable(){ 
			public void run(){ 
				System.out.println("Child Thread"); 
			} 
		}; 
		Thread t = new Thread(r);
		t.start(); 
		System.out.println("Main Thread"); 
	} 
} 
```

**Anonymous Inner class that defines inside method/constructor argument**
```java
class MyThread {
    public static void main(String[] args) {
        Thread t = new Thread(new Runnable() {
            public void run() {
                System.out.println("Child Thread");
            }
        });
        t.start();
        System.out.println("Main Thread");
    }
}
```
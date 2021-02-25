---
layout: post
title: Optional
permalink: /:collection/java/java8/optional
---

- TOC
{:toc}

<hr><br>

* Wrapper class to make a field optional, it may or may not have values.
* Used to represent a value is present or absent.
* **Optional.empty()** value instead of wrapped null, used to get rid of **NullPointerException**.
* Optional is not to be used as a member of an entity classes, because it is ***not Serializable***.

|Advantage of Java8 Optional|Disadvantages of using Optional|
|---|---|
Optional: Null checks are not required. | Not serializable making it useless for many cases.
No more Boilerplate code | Optional is a wrapper which means if you use it, you'll now have two object references where you used to have one.
No more NullPointerException at run-time. | In Some cases, it makes the debugging even worse nightmare.
Clean and neat APIs can be developed | 

|||
---|---
isPresent() | return true 
get()       | return the value. 
orElse()    |  
ifPresent() | executes a block of code if the value is present.

```java
Employee employee = new Employee(); 
Optional<Employee> op = Optional.of(employee);  //ofNullable
Optional<Employee> employee = Optional.empty();
```

# Why Optional?
**Without Optional**
```java
if (project != null) {
    ApplicationType applicationType = project.getApplicationType();
    if (applicationType != null) {
        String typeDirName = applicationType.getTypeDirName();
        if (typeDirName != null)
            System.out.println(typeDirName);
    }
}
```

**With Optional**
```java
Optional < String > optionalTypeDirName = optionalProject.flatMap(project - > project.getApplicationTypeOptional())
    .flatMap(applicationType - > applicationType.getTypeDirNameOptional());
optionalTypeDirName.ifPresent(typeDirName - > System.out.println(typeDirName));
```

```java
int min1 = Arrays.stream(new int[]{1, 2, 3, 4, 5}).min().orElse(0);
int min2 = Arrays.stream(new int[]{}).min().orElse(0);
// Stream.min() calculates the minimum value, for empty stream it returns Optional rather than null or exception.
```

# Optional Class Methods

|Optional Methods |   |
|---              |---|
|empty()	| empty Optional instance.|
|equals(Object obj) ||
|filter(Predicate<? super T> predicate) | value present and predicate ture, return Optional otherwise empty.|
|flatMap(Function<? super T ,Optional<U>> mapper) | value present, apply mapping, return result otherwise empty Optional.|
|get() | value present, returns value otherwise NoSuchElementException.|
|ifPresent(Consumer<? super T> consumer) | value present, invoke consumer otherwise do nothing.|
|isPresent()	| true if value present.|
|map(Function<? super T,? extends U> mapper)	| value present, apply mapping. and if result non-null, return Optional.|
|of(T value)	| Optional of non-null value.|
|ofNullable(T value)	| Optional of non-null value, otherwise empty Optional.|
|orElse(T other)	| return value, if present, otherwise return other.|
|orElseGet(Supplier<? extends T> other) | return value, if present, otherwise invoke other and return result.|
|orElseThrow(Supplier<? extends X> exceptionSupplier) | return value if present, otherwise throw exception to be created by the provided supplier.|
|toString() | non-empty string representation of Optional suitable for debugging.|

---
layout: post
title: To Do
permalink: /notes/todo
---

- TOC
{:toc}

<hr><br>

- array.splics(i,1);
- static class
- String.getChars

# Java

## Java Core basics
- Static block executing before everything use cases.
- Immutable with date field
- Clone - deep and shallow
- this super constructor
- Immutable Class
- https://www.journaldev.com/129/how-to-create-immutable-class-in-java/amp
- http://www.javapractices.com/topic/TopicAction.do?Id=29
- Immutable with date field
- Cloneable
- http://www.cafeaulait.org/course/week4/46.html
- https://www.geeksforgeeks.org/anonymous-inner-class-java/
- https://www.geeksforgeeks.org/flow-control-in-try-catch-finally-in-java/

## multithreading
- [Bank ATM java multithreading example](https://www.youtube.com/watch?v=0nDYk8sV_jQ){:target="_blank"}
- process vs thread
- Why multithreading
- Multithreading vs Concurrency
- Semaphore
- Countdown Latch
- Cyclic barrier
- Executor For Join
- Re-enterant Lock
- Thread - wait notify life cycle
- Concurrent hashmap
- Wait and sleep
- Iterator
- Fail fast fail safe
- Double check locking
- Semaphore
- ThreadGroup
- Thread Executors

### Fork-Join Frame work
- ForkJoinPool
- ForkJoinTask – RecursiveAction (return void)
- ForkJoinTask – RecursiveTask (return value)
- Thread Stealing pool
- invokeAll(), invoke(), execute(), submit()

## Collections
### LinkedList
- [ ] Internal implementation – DoublyLinkedList that is why ListIterator has reverse
  
### HashMap
- [ ] HashMap internal Working
- [ ] How Linked hashMap works to maintain sequence
- [ ] HashMap implementations
- [ ] Default size HashMap 

## Java8
- [ ] How jdk8 streams work internally – pipeline
- [ ] Intermediate and terminal operations
- [ ] Stream Student object as `Map<city, List<Student>>`  - [MapStringListOfValues](https://stackoverflow.com/questions/50348166/java-8-list-of-objects-to-mapstring-list-of-valuesNew features in java8
- Default methods in functional interfaces – consumer with get and andThen(default)
- Lambda expressions
- Functional Interfaces
- Function
- Predicate
- Consumer
- Supplier
- Biconsumer
- Streams – how they wotk at processor level
- Parallel stream – what, when and why
- Parallel stream – use join and fork
- Parallel stream, tradeoff and blocking calls in it
- map vs flatmap
- stream toMap `<String, List<String>>` - groupby
- splitIterator
- PrimitiveIterator
- Primitive streams
- Streams slower than normal for loop then why to use them
- Parallel vs concurrent gc
- Stream works internally
- How Java 8 linked list works, singly or doubly.
- How reverse iterator available on list if singly Linked list
- Split iterator - tryAdvance and for each remaining
- Count char Freq in java 8
- Predicate default methods
- View projection vs content projection
- Map of key, list Java 8
- Object methods on lambda expression reference
- Functional Programming

## Serialization and Externalization
- Serialization
- static and transient
- SerialVersionUID – static final
- Extrenalization
- Methods causing serialization
- Serializable is marker interface, where is write and read methods defined ?

## Java IO
- [ ] ObjectOutput stream
- [ ] Object Input Stream

## Java Uncategorized
* If serializable is marker interface, where are read and write methods defined? Who takes care of these methods.
* Prime numbers upto a given number
* Pangram – every char at least once
* Memory efficient Doubly Linked list
* Stack using queue
* Detect loop in linked list in O(n)
* Count number of set bits in binary of a digit
* Given list of string – Find count of String starting with a specific prefix
* If serializable is marker interface, where are read and write methods defined? Who takes care of these methods.
* Serialization - http://www.benchresources.net/java/serialization-in-java/ 
* Copy Constructor versus Cloning
* Even Copy Constructors Are Not Sufficient
* Shallow vs Deep Copy
* https://programmingmitra.blogspot.in/2017/01/Java-cloning-copy-constructor-versus-Object-clone-or-cloning.html
* https://programmingmitra.blogspot.in/2017/01/java-cloning-why-copy-constructors-are-not-sufficient-or-good.html
* https://programmingmitra.blogspot.in/2016/11/Java-Cloning-Types-of-Cloning-Shallow-Deep-in-Details-with-Example.html
* https://dzone.com/articles/shallow-and-deep-java-cloning
* [ ] hashcode uses 31 or prime
    - [ ] https://stackoverflow.com/questions/299304/why-does-javas-hashcode-in-string-use-31-as-a-multiplier 
    - [ ] https://computinglife.wordpress.com/2008/11/20/why-do-hash-functions-use-prime-numbers/ 
    - [ ] http://www.jusfortechies.com/java/core-java/hashcode.php 
    - [ ] https://srvaroa.github.io/jvm/java/openjdk/biased-locking/2017/01/30/hashCode.html 
* [ ] wait vs sleep
    - https://stackoverflow.com/questions/1036754/difference-between-wait-and-sleep 
    - https://infinitescript.com/2014/09/difference-between-wait-and-sleep-yield-in-java/ 
* [ ] Jackson JSON
    - https://dzone.com/articles/jackson-annotations-for-json-part-1-serialization 
* http://stackoverflow.com/questions/17263330/does-calling-a-super-constructor-from-subclasss-constructor-create-object-of-sup
* http://docs.oracle.com/javase/tutorial/java/IandI/super.html
* http://stackoverflow.com/questions/16498211/does-creating-an-instance-of-a-child-class-automatically-create-its-super-class
* http://stackoverflow.com/questions/17877615/how-many-objects-are-created-due-to-inheritance-in-java

# Coding
- [x] Print 2D array as spiral
- [ ] Print as spiral

* [ ] Angular js vs 2 vs 4
    - [ ] https://dzone.com/articles/learn-different-about-angular-1-angular-2-amp-angu 
    - [ ] https://dzone.com/articles/angular-2-vs-angular-4-features-performance 

* [ ] openssl version -a
* www.java2novice.com/java_interview_questions/servlet_destroy/
* Content Negotiation issue
    - https://spring.io/blog/2013/05/11/content-negotiation-using-spring-mvc
    - https://medium.com/@saishav_io/error-406-while-using-and-email-address-as-a-path-variable-in-spring-boot-8caaefc17c7b

# Maven
- Maven All Commands - http://tutorials.jenkov.com/maven/maven-commands.html
- mvn dependency:sources
- mvn clean install
- mvn clean install -DskipTests
- mvn dependency:tree > C:\Users\chxk7r\Desktop\temp\dependency-tree.txt

# Logging
- [ ] MDC - https://www.baeldung.com/mdc-in-log4j-2-logback
* Util Code
    - [ ] RandomStringUtils.random(length, useLetters, useNumbers);

# MicroServices
- microservices architecture
- Service Registry and discovery
- Openshift platform
- Docker
- images
- Load balancer
- Hystrix – Rate Limit + Circuit Breaker
- zipkin
- Sleuth
- batch

# Hibernate
- https://howtodoinjava.com/hibernate/hibernate-jpa-2-persistence-annotations-tutorial/
- Why ORM
- Mapping
- Inheritance
- Config xml
- Call stored procedure
- States – transient, persistent ,detached
- criteria
- Criteria projection

# Kafka
- What is kafka
- Architecture – Zookeeper, Broker, Topic, Partition, Offset
- Consumer
- Properties
- max.poll.records – default 500
- compressed.topics
- linger.ms
- batch.size
- Performance improvement by batching
- Avro as data format
- Avro schema registry
- Kafka Sreams
- measure throughput of a partition for your setup
- Advance Questions
  - Can we do batch processing in Kafka?
  - Can we stop duplicate reads in Kafka?
  - How load balancing happens?

# Spring
- Circular Dependency - http://www.baeldung.com/circular-dependencies-in-spring
- Singleton - https://www.geeksforgeeks.org/singleton-class-java/
- RequestBody and ResponseBody
- http://www.baeldung.com/spring-request-response-body

## Spring REST
- Rest Template
- http://www.baeldung.com/rest-template
- http://www.baeldung.com/how-to-use-resttemplate-with-basic-authentication-in-spring
- Stateful Stateless Concept
- https://dzone.com/articles/stateless-session-multi-tenant
- https://dzone.com/articles/how-to-make-a-stateless-session-less-authenticatio
- https://nordicapis.com/defining-stateful-vs-stateless-web-services/
- http://whatis.techtarget.com/definition/stateless-app

# JSON
- http://www.baeldung.com/jackson-object-mapper-tutorial

# Web Services
- web.xml / Deployment descriptor - https://cloud.google.com/appengine/docs/standard/java/config/webxml
- wsdl
- xsd
- jaxb
- Filter vs Intercepors - http://www.javabench.in/2011/10/java-difference-between-filter-and.html?m=1
- Soap vs REST - https://stackify.com/soap-vs-rest/amp/
- Jackson Deserialization - https://github.com/FasterXML/jackson-databind/wiki/Deserialization-Features

# Angular
- JSON obj vs js obj
- How DI works in angular
- Lifecycle hooks
- Routers
- @NgModule
- Injector in angular works
- ngRX store - component, action, reducer, store
- Pure impure functions
- Pure impure pipes
- --prod jit vs --prod --aot
- Stateful angular
- Session Store
- Custom Pipes and declarations
- JWT on angular side
- https://www.code-sample.com/2017/08/angular-5-interview-questions-and.html?m=1

# Others
* [java-logging-basics](https://www.loggly.com/ultimate-guide/java-logging-basics/)
* [java-logging-best-practices](https://stackify.com/java-logging-best-practices/)
* [Logging HTTP RESTful API](https://docs.cask.co/cdap/6.0.0/en/reference-manual/http-restful-api/logging.html)
* [Authentication and Authorization Flows](https://auth0.com/docs/flows)
* [Spring Security 4 Java API: Authorization](https://auth0.com/docs/quickstart/backend/java-spring-security/01-authorization)
* [Auth0 for B2B Multitenancy](https://auth0.com/blog/using-auth0-for-b2b-multi-and-single-tenant-saas-solutions/)
* [OAuth 2.0 and OpenID Connect (in plain English) - Youtube](https://www.youtube.com/watch?v=996OiexHze0)
* [OAuth 2.0: An Overview](https://www.youtube.com/watch?v=CPbvxxslDTU)
* [Top 5 REST API Security Guidelines](https://blog.restcase.com/top-5-rest-api-security-guidelines/)
* [Top 5 REST API Security Guidelines - DZone](https://dzone.com/articles/top-5-rest-api-security-guidelines)
* [Maven Goals and Phases](https://stackoverflow.com/questions/16205778/what-are-maven-goals-and-phases-and-what-is-their-difference#:~:targetText=If%20you%20specify%20a%20goal,will%20run%20the%20jar%20goal.)
* [API Error Handling](https://www.toptal.com/java/spring-boot-rest-api-error-handling)
* [REST Resource Naming Guide](https://restfulapi.net/resource-naming/)
* [Java 8 Streams API](https://stackify.com/streams-guide-java-8/)
* [LocalStorage, sessionStorage](https://javascript.info/localstorage)
- Elastic search
- [chmod](https://www.lifewire.com/uses-of-command-chmod-2201064){:target="_blank"}
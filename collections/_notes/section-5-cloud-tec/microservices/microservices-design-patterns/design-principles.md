---
layout: post
title: Microservice Architecture Design Principles
permalink: /:collection/microservices/design-principles
---

**What are Reactive Extensions in Microservices?**
- Reactive Extensions is also called Rx.
- It is a design pattern which allows collecting results by calling multiple services and then compile a combined response.
- Rx is a popular tool in distributed systems which works exactly opposite to legacy flows.

[9 Fundamentals to a Successful Microservice Design]( https://dzone.com/articles/9-fundamentals-to-a-successful-microservice-design)

**Fundamentals of Microservices Design**
- Define a scope
- Loose coupling
- High cohesion
- Seamless API Integration
- A unique source of Identification for every service
- Create a unique service which will act as an identifying source, much like a unique key in a database table.
- Creating the correct API and taking special care during integration.
- Restrict access to data and limit it to the required level.
- Real-Time Traffic Management - Maintain a smooth flow between requests and response.
- Automate most processes to reduce time complexity.
- Isolated data storage for each microservice
  - Keep the number of tables to a minimum level to reduce space complexity.
  - Classification of data based on the users is important and can be achieved through the Command and Query Responsibility Segregation (CQRS)
- Performing constant monitoring over external and internal APIs
  - Monitor the architecture constantly and fix any flaw when detected.
- Data stores should be separated for each microservice
  - Minimizing data tables to optimize load
- For each microservice, there should be an isolated build.
- Deploy microservices into containers.
- Servers should be treated as stateless.
- **Decentralization** – The first and foremost principle to design microservice architecture is the ability to break down the monolithic architecture into separate individual entities. These entities are known as microservices. These microservices work independent of the other system functions and all users to edit, delete or employ any functionality without affecting the system performance.
- **Scalability** – Microservices are built with an aim in mind: Performance and efficiency. In real-world problem solving, expansion and large-scale systems are crucial to the performance of any microservice ecosystem. Scalability is crucial to design microservice architecture. With the possibility of multiple fragments functioning on multiple technologies, working with larger amounts of data can be a challenge. But, proper implementation and use of Application Controllers can make scalability with microservice architecture possible.
- **Continuous delivery through DevOps Integration** – Those working in DevOps often receive microservice architecture well because of the ease of accessibility and integration of multiple technologies. To design microservice architecture one needs to focus on increasing performance and efficiency of the system. This motivates DevOps to deliver solutions faster. It also offers certain advantages over a traditional monolithic design such as ease of deployability, reliable solutions, scalability, and management. Hence, it forms a major part of the basic principles of design.

- [Reference - Microservices Design and Architecture Patterns - Edureka](https://www.youtube.com/watch?v=xuH81XGWeGQ){:target="_blank"}

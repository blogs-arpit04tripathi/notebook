---
layout: post
title: Microservices Features
permalink: /:collection/microservices/features
---

**Disadvantages of Monolithic Application**
- One small change will need you to compile and deploy the whole application.
- Scaling up needs you to make copies of whole application.
- Separation of concern is not present.
- Same coding language throughout.

**Advantages of Microservices**
- Focus on single capability only.
- Each microservice is an individual component (deployable units).
  - Frequent Independent deployments.
  - Easy to scale
-	Technology diversity i.e. can use different libraries, databases, frameworks etc.
- It gives maximum security to each of the services.
- Smaller code base is easy to maintain.
- Fault isolation i.e. a process failure should not bring whole system down.
- Better support for smaller and parallel team.
  - possible developing and deploying multiple services together.

**Disadvantages of Microservices**
-	Distributed System so hard to debug and trace the issues
-	It will increase delays due to remote calls.
-	Difficult to achieve strong consistency across services
-	ACID transactions do not span multiple processes.
-	Greater need for end to end testing
-	Required cultural changes in across teams like Dev and Ops working together even in same team.

# Features
* Independent and Autonomous services - 
* Scalability - 
* Decentralization - Decentralized Governance
* Real Time Load Balancing - 
* Availability - 
* Continuos delivery through DevOps Integration - Infrastructure automation
* Seamless API Integration and Continuos Monitoring - 
* Isolation from Failures - Design for failure
* **Fault Tolerance** - How does system behave when there is a fault, impact of fault.
* **Resilience** - How many faults can system tolerate.
* Auto-Provisioning - 
* Essential messaging frameworks
* **Low Coupling** - Coupling is the measurement of strength between the dependencies of a component.
* **High Cohesion** - degree to which how components bind together within a module is called the Cohesion.

# Best Practices to Design Microservices
- Specific business problem (capability) for each Microservice.
- Specific data store for each Microservice (table).
- Decoupled microservices.
- The code should be arranged at a similar level of maturity.
- A separate build should be designed for each Microservice.
  - Each build should be deployed into containers.
- The server should always be treated as stateless.
- Each microservice can use tools and technology as per suitability of its problem statement.
- Fault Isolation.

**Common Mistakes Made While Transitioning to Microservices**  
- Not only on development, but mistakes also often occur on the process side.
- Often the developer fails to outline the current challenges.
- Rewriting the programs that are already existing.
- Responsibilities, timeline, and boundaries not clearly defined.
- Failing to implement and figure out the scope of automation from the very beginning.
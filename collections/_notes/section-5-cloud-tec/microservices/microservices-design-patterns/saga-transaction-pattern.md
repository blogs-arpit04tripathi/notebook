---
layout: post
title: Asynchronous Messaging Pattern
permalink: /:collection/microservices/patterns/saga-transaction-pattern
---

- [Microservices Using the Saga Pattern](https://dzone.com/articles/microservices-using-saga-pattern#:~:text=The%20Saga%20Pattern%20is%20as,perform%20the%20next%20local%20transaction.){:target="_blank"}

- The Saga Pattern is as microservices architectural pattern to implement a transaction that spans multiple services.
- A saga is a sequence of local transactions.
- Each service in a saga performs its own transaction and publishes an event.
- The other services listen to that event and perform the next local transaction.
- If one transaction fails for some reason, the saga also executes compensating transactions to undo the impact of the preceding transactions.

# Types
- **Orchestration-Based Saga**
  - In this approach, there is a Saga orchestrator that manages all the transactions and directs the participant services to execute local transactions based on events. This orchestrator can also be though of as a Saga Manager.
- **Choreography-Based Saga**
  - In this approach, there is no central orchestrator. Each service participating in the Saga performs their transaction and publish events. The other services act upon those events and perform their transactions. Also, they may or not publish other events based on the situation.
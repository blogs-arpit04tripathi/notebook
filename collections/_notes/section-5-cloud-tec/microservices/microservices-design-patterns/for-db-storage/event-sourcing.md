---
layout: post
title: Event Sourcing Design Pattern
permalink: /:collection/microservices/patterns/event-sourcing
---

- How can you rely on the architecture to make a change or publish a real-time event with respect to the changes in state of the application?
- Event sourcing helps to come up from this situation by appending a new event to the list of the events every time a business entity changes its state.
- Entities like Customer may consist of numerous events.
- It is thus advised that an application saves a screenshot of the current state of an entity in order to optimize the load.
- Creates events regarding the changes in the application state.
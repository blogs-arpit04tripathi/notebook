---
layout: post
title: Command Query Responsibility Segregation (CQRS)
permalink: /:collection/microservices/patterns/cqrs
---

- In a database-per-service model, the query cannot be implemented because of the limited access to only one database.
- For a query, the requirements are based on joint database systems. But how do we query then?
- Based on the CQRS, to query single databases per service model, the application should be divided into two parts: Command and Query.
- In this model, command handles all requests related to create, update and delete while queries are taken care of through a materialized view.
- These views are updated through a stream of events.
- These events, in turn, are created using an event sourcing pattern which marks any changes in the data. These changes eventually become events.
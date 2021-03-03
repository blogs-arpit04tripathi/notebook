---
layout: post
title: Circuit Breaker
permalink: /:collection/microservices/circuit-breaker
---

**When does a circuit trips?**
- Last n requests to be considered for decision.
- How many of those requests are failing.
- timeout duration to define failure.

**When does circuit becomes normal?**
- How long after a circuit trip to try again? `sleep window`

**What to do for requests when circuit trips?**
- This is called Fallback Mechanism.
- Throw an error. (not recommended)
- Return a fallback default response. (not recommended)
- Save previous responses (cache), use it when possible.

**Key Features of Circuit Breaker Pattern**
- Failing Fast.
- Fallback Functionality.
- Automatic Recovery.
- Technology Available - Hystrix

* [Circuit Breaker Pattern - Fault Tolerant Microservices](https://www.youtube.com/watch?v=ADHcBxEXvFA)
* Used to stop the process of request and response if a service is not working.
* client invokes remote service via proxy, proxy behaves as barrier.


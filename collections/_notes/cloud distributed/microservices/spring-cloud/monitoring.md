---
layout: post
title: Monitoring
permalink: /:collection/microservices/monitoring
---

**Why Would You Need Reports and Dashboards in Microservices?**  
Reports and dashboards are mainly used to monitor and upkeep microservices. There are multiple tools that help to serve this purpose. Reports and dashboards can be used to:
-	Find out which microservices expose what resources.
-	Find out the services which are impacted whenever changes in a component occur.
-	Provide an easy point which can be accessed whenever documentation is required.
-	Versions of the components which are deployed.
-	To obtain a sense of maturity and compliance from the components.

**Explain the term ‘Continuous Monitoring’?**  
Continuous monitoring is a method which is used for searching compliance and risk issues associated with a company’s operational and financial environment. It contains human, processes, and working systems which support efficient and actual operations.

**What Is Semantic Monitoring?**  
-	It combines monitoring of the entire application along with automated tests. The primary benefit of Semantic Monitoring is to find out the factors which are more profitable to your business.
-	Semantic monitoring along with service layer monitoring approaches monitoring of microservices from a business point of view. Once an issue is detected, they allow faster isolation and bug triaging, thereby reducing the main time required to repair. It triages the service layer and transaction layer to figure out the transactions affected by availability or poor performance.

**How Will You Monitor Multiple Microservices For Various Indicators Like Health?**  
Spring Boot provides actuator endpoints to monitor metrics of individual microservices. These endpoints are very helpful for getting information about applications like if they are up, if their components like database etc are working good. But a major drawback or difficulty about using actuator enpoints is that we have to individually hit the enpoints for applications to know their status or health. Imagine microservices involving 50 applications, the admin will have to hit the actuator endpoints of all 50 applications. To help us deal with this situation, we will be using open source project located at Built on top of Spring Boot Actuator, it provides a web UI to enable us visualize the metrics of multiple applications.


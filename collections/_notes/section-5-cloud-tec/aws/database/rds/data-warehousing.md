---
layout: post
title: Data Warehousing
permalink: /:collection/aws/rds/data-warehousing
---

* Used for business intelligence. Tool slike Cognos, Jaspersoft, SQLServer Reporting Services, Oracle Hyperion, and SAP NetWeaver.
* Used to pull in very large and complex data sets. Usually used by management to do queries in data (such as current performance vs targets, etc.)

# OLTP vs OLAP
* Online Transaction Processing(OLTP) differs from Online Analytics Processing(OLAP) in terms of the types of queries you will run.
* OLTP Example
    - Frequent but simple transactions
    - Order number 2120354 pulls up a row of data such as Name, Date, Address to Deliver to, Delivery status etc.
* OLAP Example
    - RedShift
    - Infrequent but complex transactions
    - Net profit of EMEA and Pacific for Digital Radio Product pulls in large number of records.
    - Sum of radios sold in EMEA.
    - Unit cost of Radio in each region.
    - Sales price - unit cost.
* Database Warehousing DB use a different type of architecture both from a DB perspective and infrastructure layer.

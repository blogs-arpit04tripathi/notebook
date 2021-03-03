---
layout: post
title: DAX - DDB Accelerator
permalink: /:collection/aws/ddb/dax
---

- Fully managed, clustured in-memory cache for DynamoDB.
- Delivers upto 10x read performance improvement.
- Microsecond performance for millions of requests per second.
- Ideal for Read-Heavy and bursty workloads.
- eg. auction applications, gaming and retail sites during black friday promotions.

# How Does it Work
- DAX is write-through caching service - this means data is written to the cache as well as the backend store at the same time.
- Allows you point your DynamoDB API calls at the DAX clusture.
- If item being queried is in the cache(cache hit), DAX returns the result to application.
- If item not available in cache(cache miss) then DAX performs an Eventually Consistent GetItem operation against DynamoDB.
- Retrieval of Data from DAX reduces the read load on DynamoDB Tables.
- May be able to reduce Provisioned Read Capacity.

# What is it Suitable for
- Caters for Eventually Consistent reads only - so not suitable for applications that require Strongly Consistent Reads.
- Write Intensive applications.
- Applications that do not perform many read operations.
- Applications that do not require microsecond response times.

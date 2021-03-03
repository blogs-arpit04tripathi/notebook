---
layout: post
title: Scan vs Query
permalink: /:collection/aws/ddb/scan-vs-query
---

- TOC
{:toc}

---

# Query
- Query operation inda item in table based on primary key attribute and value to search for.
- use optional sort key name and value to refine the results.
- by default, query returns all the attributes for the items but you can use the `projection expression` parameter to return only specific attributes.
- results are always sorted by the sort key
    - numeric order - ascending order
    - ASCII character code values
- You can reverse the order by setting the `ScanIndexForward` parameter to false.
- by default, queries are eventually consistent
- you need to explicitly set the query to be Strongly Consistent.

# Scan
- Scan operation examines every item in the table.
- By default returns all data attributes.
- `projectionExpression` parameter to refine the scan to only return the attributes you want.

# Query or Scan
- Query is much more efficient than scan.
- Scan dumps entire table, then filters out the values to provide the desired results - removing unwanted data.
    - Additional step of removing data you don't want.
- As table grows, Scan operation takes longer.
- Scan operation on large table can use up the provisioned throughput in just a single operation.

# How to improve Performance
- You can reduce the impact of a query or scan by setting smaller page size which uses fewer read operations.
- Large number of smaller operations will allow other requests to succeed without throttling.
- Avoid using scan operations, instead you can design tables in a way that you can use the query, get or BatchGetItem APIs.
- by default, a scan operation processes data sequencially in returning 1MB increments before moving on to retrieve next 1MB of data. It can scan only 1 partiton at a time.
- You can configure dynamoDB to use parallel scans by logically dividing a table or index into segments and scanning each segment in parallel.
- best to avoid parallel scans if your table or index is already incurring heavy read/write activity from other applications.

---
layout: post
title: API Throttling
permalink: /:collection/aws/api-gateway/api-throttling
---

- By default, API Gateway limits the steady state request rate to 10,000 requests per second (rps).
- Maximum concurrent requests is 5000 requests ***across all APIs within an AWS account***.
- If you go over 10,000 rps or 5000 concurrent requests, you will receive HTTP status code 429 - Too Many Request error response.
- Examples
    - 10,000 rps evenly distributed in 1 sec --> API Gateway processes all without dropping any.
    - 10,000 requests in first millisecond, API Gateway serves 5,000 of those requests and throttles the rest in the 1 sec period.
    - 5,000 requests in first millisecond and remaining 5000 spread evenly in 999 milliseconds, API Gateway processes all 10,000 requests without 429 Too Many Requests error response.
- You can increase the throttling limit of API Gateway, but you incurr additional charges.

# SOAP Webservice Passthrough
- You can configure API Gateway as a SOAP web service passthrough.

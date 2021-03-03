---
layout: post
title: API Caching
permalink: /:collection/aws/api-gateway/api-caching
---

- You can allow API caching in API gateway to cache your endpoint response.
- Caching to reduce the number of calls and latency.
- When you enable caching for a stage, API Gateway caches responses from your endpoint for specified TTL(Time To Live) period, in seconds.
- API Gateway then responds to request by looking up the endpoint response from the cache instead of making a request to your endpoint.

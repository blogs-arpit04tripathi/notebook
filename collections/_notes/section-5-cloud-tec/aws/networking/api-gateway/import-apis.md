---
layout: post
title: Import APIs
permalink: /:collection/aws/api-gateway/import-apis
---

- Use API Gateway Import API feature to import API from an external definition file into API Gateway.
- Supports Swagger 2.0 definition files.
- To import API
    - Create new by submitting a POST request with swagger definition file as payload and endpoint configuration.
    - Update an existing API using PUT request with swagger definition file as payload.
        - Update the existing file either by overwriting with new defintion file or merge defintion with existing file. You can specify the options using a mode query parameter in the request URL.

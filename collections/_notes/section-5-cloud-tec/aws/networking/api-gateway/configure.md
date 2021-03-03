---
layout: post
title: How to Configure API Gateway
permalink: /:collection/aws/api-gateway/configure
---

- Define an API(container)
- Define Resources and nested Resources(URL paths)
- For each Resource:
    - Select supported HTTP methods (verbs)
    - Set security
    - Choose target (such as EC2, Lambda, DynamoDB etc.)
    - Set request and response transformations
- Deploy API to a Stage
    - Use api gaetway domain by default
    - Can use custom domain
    - Now supports AWS Certificate Manager: free SSL/TLS certs

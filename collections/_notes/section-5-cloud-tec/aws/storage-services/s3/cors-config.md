---
layout: post
title: CORS Configuration
permalink: /:collection/aws/s3/cors-config
---

- Cross origin resource sharing
- S3 buckets could be used to host a static website.
    - create public bucket
    - properties --> static website hosting
        - index.html
        - error.html
- to enable cors
    - go to target bucket being accessed
    - permissions --> CORS configuration --> update Allowed Origin
- Use Case - Static Website
    - put images, js, html in different buckets

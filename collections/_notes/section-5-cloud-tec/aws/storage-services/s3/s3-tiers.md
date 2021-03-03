---
layout: post
title: S3 Storage Tiers Or Classes
permalink: /:collection/aws/s3/tiers
---

- TOC
{:toc}

---

# S3
* 99.99% Availability
* 99.999999999% Durability
* Stored redundantly across multiple devices in multiple facilities.
* Designed to sustain loss of 2 facilities concurrently.

# S3 IA (Infrequently Accessed)
* For data that is accessed less frequently, but requires rapid access when needed.
* Lower price than S3 but you are charged a retrieval fee.

# S3 One Zone IA
* Same as IA however data is stored in a single Availability zone.
* 99.5% Availability
* 99.999999999% Durability
* Costs 20% lesser than regular S3-IA.

# Reduced Redundancy Storage
* 99.99% availability and durability
* Used for data that can be created if lost, eg. thumbnails.
* Amazon suggesting to use normal S3 rather than Reduced Redundancy Storage, adjustments made in pricing
* May phase out in future

# Glacier
* Very cheap
* Used for archival only
* Optimised for data that is infrequently accessed
* It takes 3-5 hours to restore from glacier.

![s3-tiers]({{site.cdn}}/aws/s3/s3-tiers.png)

# S3 Intelligent Tiering
* Unknown or unpredictable access patterns
* 2 tiers - frequent and infrequent access
* Automatically moves your data to most cost-effective tier based on how frequently you access each object.
* frequent access tier object not accessed for 30 days --> move to infrequent tier.
* as soon as infrequent tier object is accessed, it is moved to frequent access tier.
* 99.999999999% durability
* 99.9% availability
* Optimizes cost
* No fees for accessing your data but small monthly fee for monitoring/automation $0.0025 per 1000 objects.

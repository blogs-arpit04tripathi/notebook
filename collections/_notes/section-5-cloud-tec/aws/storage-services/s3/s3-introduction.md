---
layout: post
title: S3 Introduction
permalink: /:collection/aws/s3/introduction
---


* Simple Storage Service
* Provides developers and IT teams with secure, durable, highly-scalable object storage.
* For files, images etc. not for Operating systems or databases.
* Object based storage.
* Data is spread across multiple devices and facilities.
* Files can be from 0 Bytes to 5 TB.
* Unlimited Storage.
* Files are stored in Buckets(similar to folder).
* S3 is a universal namespace ie. names must be unique globally same as DNS.
* ex. https://s3-eu-west-1.amazonaws.com/acloudguru
* HTTP 200 on successful upload for cli.
* Read after write consistency for PUTS of new objects.
* Eventual consistency for overwrite PUTS and DELETES.(can take some time to propagate).
* S3 is Object based
    - Key - name of the object
    - Value - the data, made up of sequence of bytes.
    - Version ID
    - Metadata - Data about data being stored
    - Subresources - bucket specific configuration
        - bucket policies, Access control list.
        - Cross origin resource sharing(CORS).
        - Transfer acceleration
* Built for 99.99% Availability - time for which service is available
    - Amazon guarantees 99.9% availability.
* Amazon guarantees 99.999999999% durability - Amount of data that will not corrupt.
* Tiered Storage
* Lifecycle management
* Versioning
* Encryption
* Secure your data - Access Control Lists and Bucket Policies

# References
* [S3 FAQ - AWS](https://aws.amazon.com/s3/faqs/)

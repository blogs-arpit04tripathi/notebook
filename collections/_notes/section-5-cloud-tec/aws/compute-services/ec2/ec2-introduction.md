---
layout: post
title: EC2 Introduction
permalink: /:collection/aws/ec2/introduction
---

* Amazon Elastic Cloud Compute
* Provides resizable compute capacity in the cloud.
* New Server Instance in minutes, allowing to scale capacity up or down as required.
* Pay only for capacity you use.
* Think of it as virtual server in the cloud

# Types of EC2
- On Demand
- Reserved
- Spot
- Dedicated Host

# On Demand
- Pay a fixed rate per hour with no commitment.
- No upfront payments or long-term commitment.
- For applications with short term, spiky or unpredicatable workloads that can't be interrpted.

# Reserved
- Provides you with a capacity reservation, significant discount on hourly charges.
- 1 or 3 years Term.
- Applications with steady state or predictable usage.
- Applications that require reserved capacity.
- Users can make upfront payments for further cost reduction
    - Standard RI : Upto 75% off on-demand
    - Convertible RI : Upto 54% off on-demand
        - Can change attributes of RI as long as new RI is of equal or greater value.
    - Scheduled RI - Available to launch within time window you reserve.
        - Allows you to match capacity for predicatable recurring schedule that requires only a fraction of day/month/year, ex. month end sale.

# Spot
- Bid prices for instance capacity, greater savings if your application have flexibile start and end times.
- For Genomic companies or pharmaceutical companies or chemical companies use this for doing huge amount of computing on 4 am of sunday morning to reduce cost.
- If a spot isntance is terminated by EC2, you will not be charged for partial hour of usage. However, if you terminate the instance yourself, you will be charged for the complete hour in which the instance ran.

# Dedicated Host
- Physical EC2 server for dedicated use, can help reduce cost by allowing you to use your existing server-bound software licenses.
- Used for regulatory requirements that may support multi-tenant virtualization.
- Great for licensing which does not support multi tenancy or cloud deployments.
- Can be purchased on-demand(hourly).
- Can be purchaed as a reservation for upto 70% off the on-demand price.

---
layout: post
title: Multi Tenancy
permalink: /:collection/auth0/multi-tenancy
---

# Multi Tenancy
- Blog - https://auth0.com/blog/how-to-use-auth0-to-manage-your-multi-tenancy-application/
- Select connection - https://auth0.com/docs/libraries/lock/v11/selecting-the-connection-for-multiple-logins
- Auth0 for Multi Tenant - https://auth0.com/docs/design/using-auth0-with-multi-tenant-apps
- UseCase Product0 - https://auth0.com/blog/using-auth0-for-b2b-multi-and-single-tenant-saas-solutions/

* Multi-tenant - One instance, multiple customers.
* Single-tenant - One instance, one customer.

# Tenant
- a group of users who share access to that application instance.
- could be a company with multiple employees, all who have access to your SaaS service.

In a multi-tenant architecture, a single instance of your application would be shared across multiple companies (tenants), and across multiple employees within those companies.

Every tenant would however have a dedicated share of that instance, and multi-tenant application can then be customized for each specific tenant's need, in particular:
- **Branding** - Each instance would likely need to be “skinned” to fit with the branding of the organization. This is akin to how Lock can be customized for each user's login page.
- **Functionality** - Each tenant may require certain workflow changes that fit better with their business.
- **Access Control** - Each tenant will want to set the permissions, rights, and roles of their users independently.

# Benefits of Multi-Tenancy (mainly SaaS company)
- Scalability
    - In single tenancy architecture, there is overhead associated with spooling up each application instance.
    - Example - Total 10 tenants and each tenant needed 1.1 servers for their requirement then you need total 20 servers as each tenant demands dedicated server.
- Data Hiding
    - Easier to handle and utilize data when it is aggregated in a single location, so running queries across multiple tenants and analysing trends is simpler.
- Release Management
    - Single codebase for all tenants, hence fix is released to all tenants in one go.
        
# Why Multi-Tenancy Is Difficult
- it requires significant planning and forethought to go into the initial coding.
- As there is no physical separation between different tenants like there would be with single-tenant architectures, all the separation has to be resolved in code.
- Developers have to :
    - determine the tenant a request was intended for
    - protect against data leakage
    - isolate configurations
    - run individual logging and background tasks per tenant
- Additionally, as each tenant’s data is stored together, significant security testing is required to make sure each tenant has access to only their data.

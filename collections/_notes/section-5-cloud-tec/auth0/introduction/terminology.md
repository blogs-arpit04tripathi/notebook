---
layout: post
title: Auth0 Terminology
permalink: /:collection/auth0/terminology
---

- [Auth0 Glossary](https://auth0.com/docs/glossary){:target="_blank"}

# Tenant
- Tenant is a term borrowed from software multitenancy. It refers to an architecture where a single software instance serves multiple tenants. In Auth0, a tenant is logically isolated. No tenant can access the data of another tenant, even though multiple tenants might be running on the same machine.
- Characteristics
    - The tenant name has to be unique. It will be used to create your personal domain.
	- The tenant name must be all lowercase.
	- The tenant name cannot be changed after creation.
    - You can create more than one tenant; in fact, you are encouraged to do so for each environment you have (such as Development, Staging, or Production).

# Domains
- Auth0 domains, base URL you will use to access our API and the URL where your users are redirected in order to authenticate.
- Pattern : <YOUR-TENANT-NAME>.auth0.com

# Application
- Refers to third-party applications that need access to restricted resources owned by resource owner without sharing credentials with the third party. 
- you must register each application.
- On creation, Each App have a generated client ID (Sharable) and client Secret (confidential).
- Types of Applications:
    - **Regular Web App** - Traditional web apps that perform most of their application logic on the server (such as Express.js or ASP.NET).
	- **Single-page app(SPA)** - JavaScript apps that perform most of their user interface logic in a web browser, communicating with a web server primarily using APIs (such as AngularJS + Node.js or React).
	- **Native App** - Mobile or Desktop apps that run natively in a device (such as iOS or Android).
	- **Machine-to-Machine** - Non-interactive apps, such as command-line tools, daemons, IoT devices, or services running on your back-end. Typically, you use this option if you have a service that requires access to an API.
- Auth0 provides many different authentication and authorization grant types or flows and allows you to indicate which grant types are appropriate based on the `grant_types` property of your Auth0-registered app.

**Can the app securely hold credentials?**
- Confidential apps can hold credentials securely, require a trusted backend server to store the secret(s).
- while public apps cannot.

**Who owns the app?**
- First-party apps -controlled by the same organization or person that owns the Auth0 domain.
- Third-party apps - external parties or partners to securely access protected resources behind your API.

# Connection
- Auth0 sits between your app and the identity provider that authenticates your users (such as Google or Facebook). Through this level of abstraction, Auth0 keeps your app isolated from any changes of the provider's implementation.
- This relationship between Auth0 and the identity provider is referred to as a Connection.
- Connections are sources of users and they can be of the following types:
	- Database connections: Users log in with username and passwords, stored either in the Auth0 cloud or your own database
	- Social logins: Google, Facebook, Twitter, and more
	- Enterprise directories: LDAP, G Suite, Office 365, ADFS, AD, SAML-P, WS-Federation, and more
	- Passwordless systems: Users log in with one-time codes, sent via SMS or email
- Each connection can be shared among multiple applications. You can configure any number of connections, and then choose which of them to enable for each application.

# Rules

> Read more about [Rules](https://auth0.com/docs/rules)

- Configure custom JavaScript snippets that are executed in Auth0 as part of the transaction every time a user authenticates to your application. 
- You can call external APIs, filter which users can login to your application, use a whitelist, geolocated access or anything.

# Hooks

> Read more about [Hooks](https://auth0.com/docs/hooks)

- Configure Node.js code that is executed against extensibility points (which are comparable to webhooks that come with a server). 
- This way you can customize the behaviour of Auth0 when you use Database Connections

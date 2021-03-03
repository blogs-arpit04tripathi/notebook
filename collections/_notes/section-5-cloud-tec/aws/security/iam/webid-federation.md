---
layout: post
title: Web Identity Federation
permalink: /:collection/aws/iam/webid-federation
---

- Web Identity Federation gives your user access to AWS resources after they have succesfully authenticated with a web-based identity provider like Amazon, Facebook or Google.
- After successful authentication, user recieves an authentication code from the web identity provider, which they trade for temporary AWS security credentials.

# Amazon Cognito
Provides web identity federation with following features
- Signup and Signin to your apps.
- Access for guest users.
- Acts as an identitiy broker between your application and web id providers, so you don't need to write any additional code.
- Synchronizes user data for multiple devices.
- Recommended for all mobile applications AWS services.

Cognito brokers between your application and FB or Google to provide temporary credentials which map to an IAM role allowing access to the required resources.

No need for application to embed or store AWS credentials locally on the device and it gives users a seamless experience across all mobile devices.

# Cognito User Pools
- User Pools are directories used to manage sign-up and sign-in fucntionality for mobile and web applications.
- Users can signin directly to the User Pool or indirectly via ID Provider. Cognito acts as an identity broker between the ID Provider and AWS. Successful authentication generates number of JWT.
- Identity Pools enable you to create unique identities for your users and authenticate them with identity providers. With and identity, you can obtain temporary. limit-privilege AWS credentials to access other AWS services.

# Push Synchronization
- Cognito tracks the association between user identity and the various different devices they sign-in from.
- To provide seamless user experience for your application, Cognito uses Push Synchronization to push updates and synchronize user data across multiple devices.
- Amazon SNS is used to send a silent push notification to all your devices associated with a given user identity whenever data stored in the cloud changes.

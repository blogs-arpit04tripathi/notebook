---
layout: post
title: Microservices Authentication
permalink: /:collection/microservices/authentication
---

**What Is OAuth?**  
Open Authorization Protocol, otherwise known as OAuth, helps to access client applications using third-party protocols like Facebook, GitHub, etc., via HTTP. You can also share resources between different sites without the requirement of credentials.
OAuth allows the account information of the end user to be used by a third-party like Facebook while keeping it secure (without using or exposing the user’s password). It acts more like an intermediary on the user’s behalf while providing a token to the server for accessing the required information.

**What Are the Different Types of Two-Factor Authentication?**  
There are three types of credentials required for performing two-factor authentication.
1.	A thing that you know – like password or pin or screen lock pattern.
2.	A physical credential that you have – like OTP or phone or an ATM card, in other words, any kind of credential that you have in an external or third-party device.
3.	Your physical identity – like voice authentication or biometric security, like a fingerprint or eye scanner.

**What Is a Client Certificate?**  
This is a type of digital certificate usually used by client systems for making a request that is authenticated by a remote server. It plays an important role in authentication designs that are mutual and provides strong assurance of the identity of a requester. However, you should have a fully configured backend service for authenticating your client certificate.

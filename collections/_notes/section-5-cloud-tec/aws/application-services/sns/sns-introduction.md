---
layout: post
title: SNS Introduction
permalink: /:collection/aws/sns/introduction
---

- AWS service to setup, operate and send notifications from the cloud.
- Provides developers with highly scalable, flexible and cost effective capability to publish messages from an application and deliver them to subscribers or other applications.
- Can have push notifications from all your devices - Apple, Google, Fire OS ,Windows and android devices.
- Apart from pushing cloud notifications directly to mobile, you can deliver notifications by sms text messages or email to Amazon SQS queues or to any Http Endpoint.
- SNS notifications can also trigger lambda functions (subscribed to SNS topic), with payload of published message.
- Lambda can perform operation on payload, publish message to another SNS topic or send message to other AWS service.

# SNS Topics
- Allows to group multiple recipients using topics.
- A topic is an "access point" for allowing recipients to dynamically subscribe for identical copies of the same notification.
- One topic can support deliveries to multiple endpoint types - you can group together IOS, Android and SMS recipients. When you publish once to a topic, SNS delivers appropriately formatted copies of your message to each subscriber.
- To prevent messages from being lost, all messages published to SNS are stored redundantly across multiple availability zones.
- SNS uses publish subscribe messaging paradiagm using push notifications eliminating polling.

# SNS Benefits
- Instantaneous push-based delivery (no polling)
- simple api and easy integration with applications.
- Flexible message delivery across multiple transport protocols.
- Inexpensive, pay-as-you-go model with no upfront costs.
- Web based AWS management console offers the simplicity of a point-and-click interface.

# SNS Pricing
- 0.5$ per million SNS requests
- 0.5$ per million SNS deliveries over http.
- 0.75$ per 100 notifications for SMS.
- 20$ per million notification deliveries over email.

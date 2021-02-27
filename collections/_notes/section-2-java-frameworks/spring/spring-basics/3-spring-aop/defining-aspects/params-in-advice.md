---
layout: post
title: Parameters in advice
permalink: /:collection/spring/aop/params-in-advice
---

![]({{site.cdn}}/spring/spring-aop/advice-with-parameters.png)

- The args(trackNumber)
  - indicates that any int argument passed to playTrack() should also be passed into the advice.
  - parameter name (trackNumber), same in pointcut method signature and actual method sugnature.

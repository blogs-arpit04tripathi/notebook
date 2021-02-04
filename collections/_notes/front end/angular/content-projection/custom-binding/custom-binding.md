---
layout: post
title: Custom Binding - Property and Event
permalink: /:collection/angular/custom-binding
---

- app-root - contains servers array, app-server-edit, list of app-server-element
- app-server-element - takes property as input
- app-server-creator - output event on addition of server to app-root

> Here, app-server-creator emits event to app-root and then app-root pushes it down to app-server-element, this creates a chain of output and input.

> For lengthy chains, use of service to share data is recommended.

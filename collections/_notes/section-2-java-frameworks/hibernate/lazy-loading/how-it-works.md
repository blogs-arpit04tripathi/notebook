---
layout: post
title: How lazy loading works in hibernate
permalink: /:collection/hibernate/lazy-loading/how-it-works
---

The simplest way that Hibernate can apply lazy load behavior upon the entities and associations is **by providing a proxy implementation** of them. Hibernate intercepts calls to the entity by substituting a proxy for it derived from the entity’s class. Where the requested information is missing, it will be loaded from the database before control is ceded to the parent entity’s implementation.

Please note that when the association is represented as a collection class, then a wrapper (essentially a proxy for the collection, rather than for the entities that it contains) is created and substituted for the original collection. When you access this collection proxy then what you get inside returned proxy collection are not proxy entities; rather they are actual entities. You need not to put much pressure on understanding this concept because on runtime it hardly matters.

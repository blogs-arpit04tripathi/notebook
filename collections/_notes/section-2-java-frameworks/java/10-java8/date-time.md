---
layout: post
title: Date and Time API
permalink: /:collection/java/java8/date-time
---

**Why new Date and Time API in Java 8**  
* existing java.util.Date and SimpleDateFormatter aren’t thread-safe, leading to potential concurrency issues for users.
* Poor API design of old Java Data API, years in java.util.Date start at 1900, months at 1, days at 0 which is not very intuitive.
* These issues made third-party date and time libraries, such as Joda-Time.
* A new date and time API, free of these problems, added in package ***java.time***.

**How can we get duration between two dates or time in Java 8?**  
* new class Duration that provides the utility of computing duration between two dates.
* Duration.between(date1, date2) to get the time period in hours, mins, days etc. between date1 and date2.

**How can we get current time by using Date/Time API of Java 8?**  
* Clock class to get the current time, instead of System.currentTimeMillis()
* create a Clock object and call millis() to get the current time in milliseconds.
* instant() on Clock object to get the current time in a readable format.

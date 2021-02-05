---
layout: post
title: Uber System Design
permalink: /:collection/system-design/scalable/uber
---

# Reference
- [Uber](https://www.youtube.com/watch?v=J3DY3Te3A_A){:target="_blank"}
- [Design Patterns - Cristopher Okhravi](https://www.youtube.com/watch?v=v9ejT8FO-7I&list=PLrhzvIcii6GNjpARdnO4ueTUAVR9eMBpc)
- [design-patterns-for-humans](https://github.com/kamranahmedse/design-patterns-for-humans)
- [awesome-system-design](https://github.com/madd86/awesome-system-design)

# Introduction

1. Extensible
2. Maintainable
3. Testable

> 12 Factor App - website

# HLD (High Level Design)
- Consistent hashing
- LB
- CAP
- Sharding
- Vertical vs horizantal scale
- caching and cdn
- message queues

# LLD (Low Level Design)
- OOP (Depth)
- Design Patterns

Programming Paradigm
- Functional
- OOP
- event driven
- data oriented
- aspect oriented
- declarative - sql

Gather Requirements
- Riders can book a cab
- Rider can see nearby cab's location
- Once booked, both rider and driver can see each other location until the ride finishes
- Each cab must have details like license, color, brand, driver details
- When booking, only cabs within max radius are shown
- ETA is calculated based on the eucledian distance + 50%
- Multiple types of booking - XL, Pool, Prime, Go, Outstation
- Registration for drivers and riders
- Update cab's location every 10 seconds
- Driver can turn off his availability
- Rider can see history of bookings and upcoming bookings
- Driver can end the trip/ rider can cancel
- OTP
- Driver must accept the ride.
- Estimated and actual cost of ride.

Use Cases
- Actors - Rider, Driver, Internal Employee (Employees)
- Entities
  - Finding the nouns
  - Rider, cab, driver, booking/ride, OTP, Payment, Payment Receipt

Service
- OTP Service
- registration service
- Pricing Strategy
- Matching Strategy
- ETA Service
- Payment Service
- Notification Service
- location service
- tracking service
- Payment Gateway

Driver Entity
- Name
- Contact
- License
- Ratings
- Availability

Cab
- Number
- Brand
- Model
- Color
- cab type
- ac/non-ac
- Capacity

Rider
- Name
- Phone
- Gender
- profile
- Preferred Payment
- Prefered cab type

Trip
- Origin
- Dest
- Estimated cost
- Final Cost
- Trip Type - oustation, pool, rental
- status
- otp

Location
- latitude
- longitude
- zipcode
- landmark
- city
- state
- country

Relationships
- Driver <-> Cab (1-on-1)
- Driver <-> location (1-on-1)
- Driver <->> Booking (1-to-Many)
- Cab <<-> Cab Type
- Rider <<->> Booking
- Rider <<-> Locations
- Trip <-> Driver
- Trip <->> Rider
- Booking <<->> Location
- Location <->> Booking
- Booking <-> OTP
- Booking <-> Status
- Booking <->> Payment Receipt
- Rider <->> Booking
- Trip <->> Booking

For PUBG Type games, location update can be done by persistence connections like socket.


3 Anomalies
- Insert Anomaly
- Delete Anomaly
- Update Anomaly
- 
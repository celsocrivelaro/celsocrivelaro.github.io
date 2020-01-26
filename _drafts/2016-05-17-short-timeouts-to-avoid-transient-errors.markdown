---
layout: post
title: Short timeouts to avoid transient errors
tags: [archicteture]
date: 2016-05-17 10:00:00 -0300
author: Celso Crivelaro
---

As a developer, one of the worst problems in when I maitain some software are transient errors. 

Oftenly, they happen in two forms:

1. In some moments the system runs slow

You have no idea what is happening, the users are strugling against the system to have their tasks done every day.
Looking for troubles in application log, nothing.

2. Strange problems happen in rush hour

As car traffic, you platform has one or more rush hour, whenever the most of users are running their tasks at the same time.

# Use short timeouts!

Today, any application integrates with others, being Databse the most used at all. Other cases are APIs, DNS, Network Services, etc.

Slowness may happen in 2 situations: 

1. Your access to the service isn't available: This may happen due a network failure, a hop dropping packages

Never trust in network! Even private networks are not reliable and it gets worse if we are running over the Internet. 

2. The service is overloaded
This is the most frequent problem. This happens 

When it's an internal service, 


---
layout: post
title: When and how to automate external resources testing 
categories: [testing]
tags: [testing]
date: 2017-12-16 09:00:36 -0200
author: Celso Crivelaro
description: What should I consider External Resources? Some examples to be tested and the issues envolved.
---

Always developers come across with external integrations in a large software such as payment, trackers, APIs and file storage. When testing, traditional questions rise up: should I connect directly to this external service? Should I test with mocks or direct connections? How to prepare data on the other software to be integrated?

There are passionate opinions pending to Yes, you must connect or No, never connect to third party services. 

By my experience, there is no simple answer and the situation changes in every project. So, I created a personal guide and I hope it may help you to decide when to test and how to do it.

I divided this subject in a series of articles:

* What is an External Service
* When to connect to an external service when testing
* When not connect when testing and alternatives
* How to make a simulator 
* Testing network conditions with Mock Server

## First of all, what I consider as an external resource

I consider as external resource everything with an I/O operation, besides user interaction, so when a user connects to your app server by HTTP, I do not considered as an external resource. 

In this logic, your app acts as a client to the external service (not always, like web hooks, but I think you got the ideia 😉 ). Another consideration is the service becoming unexpected unavailable, so I should consider failures at any moment.

Some examples of what can be an external resource:

* **OS file services**: Saving in disk is an old and simple case since the beginning of computing, however, in a large and long term software. But the  times changed and today we work in Cloud Servers and PaaS such as Heroku, whose disks are totally ephemeral and your app is moved up any moment.
    * Common issues: 
        * Disk is full
        * Directory does not exists
        * Permissions were revoked
        * File to be opened is not present

* **OS network services**: STMP is a traditional protocol and mail servers are a rock in availability. However, the OS may kill one of these services or simply the port in OS can be blocked by an Firewall;
    * Common issues:
        * Process were killed by OS
        * Server is not responding
        * Port is blocked by Firewall
        * Timeouts

* **Third party Systems**: services running in other computers and communicating by  HTTP, FTP, S3 and other protocols. Here the list is large: Mandrill, PayPal. Here the challenge is testing an integration with production running service by other company.
    * Common issues:
        * Services don’t provide a sandbox environment for tests
        * Hard to check if the service in tests end-to-end
        * Nature of service such as Payment
        * Services change their state
        * Undoable actions

* **Services in our network**: Services or microservices should be in-house are easier to test, isn’t ? Not really as long as you have lesser resources (time, money and people) than a company that focus on a product. Besides the same issues from third party systems, keep an infrastructure is an additional challenge.
    * Common issues:
        * Costs of operation
        * Deploy a test environment
        * End-to-end or alone
        * Change other service’s state

In next article, I show what to take account when testing an external resource and when I should automate those tests.

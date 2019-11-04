---
layout: post
title:  "Going cloud native"
author: chandan
categories: [ cloud-native]
image: assets/images/containers.jpg
types: [post]
published: true
---

This post is summary of the learnings in the quest of understanding cloud-native applications.
Pivotal defines it as follows --
Cloud-native is an approach to building and running applications that exploits the advantages of the cloud computing delivery model. Cloud-native is about how applications are created and deployed, not where.

> Cloud-Native = (Microservices Right way + Continusous Delivery + DevOps Culture)


Other definitions are more or less similar to this. This definition was not enough for me to know whether the application that we are building, conform to the cloud-native way of developing software. So I made a list of things I had to avoid. And the list is somewhat like this.

##### 1. Don’t be unpredictable
So how do I write predictably? Write small, release small. Write “contract” defined software. Embrace microservices. (microservices solve some problems and bring some other side-effects along with it.)

Benefits?? — faster builds, quick churn out of features, easy modification.
##### 2. Don’t be OS dependent
Reduce dependency on the underlying Operating System, hardware, storage etc. We chose cross-platform Java for obvious reasons and this is on a similar front. How do I achieve this? — embrace containers ( docker ). Instead of shipping code as modules/packages, ship code embedded containers.

Benefits?? — Easy movement of applications, easy scaling.
##### 3. No Waterfall
Waterfall model of software development is rigid, ships product at once, requires more time. Probable business loss. Develop software iteratively, embrace agile methodologies setting up continuous integration and continuous deployment pipeline.
##### 4. Recovery Time
Recovery(from failures, restarts) time should be less. Choose containers instead of VMs. VM based infrastructure is slow and inefficient, long boot up time.

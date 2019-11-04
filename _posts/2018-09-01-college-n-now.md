---
layout: post
title:  "College and now: on completion of a year"
author: chandan
categories: [ engineering, views]
image: assets/images/college-now-1.jpeg
types: [post]
published: true
---
It has been a little more than a year since I have left college and joined the industry. In this little period, I sensed things that require a different way of looking. I realized that I do things in a different way than I would have done them as a college grad. I thought I’d share my experiences and lesson learned.


## Then And Now

The “It Works!” moment in me is no longer enough. I realized soon that its not about just getting it to work when real users(in thousands) are going to use it. I cannot ask users to stop using my application, and say the application will be back in a while. The risk of losing users taught me to think through various situations, edge cases etc. and be prepared for the worst scenarios.

> One size doesn’t fit all.

I have been using relational databases for almost all usecases in my academic years, until recently when I discovered the NoSQL paradigm. While exploring NoSQL databases/datastores(eg. mongodb), I can recall ending up doing normalized nosql. To be very honest I tried to apply the concepts taught in traditional database management courses. Choosing tools, databases was not given a proper thought while doing my college projects. When I look back it looks like an effort inorder to realize the concepts. Now, I would ask couple of questions like, how many people will use it? What would be the read and write pattern? what would be the volume of data? How consistent and available should it be? etc. Such questions help me understand few of the vital aspects like consistency, availability, load etc.

If the domain allows, I will definitely use the freedom and richness that noSql databases/datastores provides. I might very well use more than one database/datastore. I might use redis for caching(session store), etcd/zookeeper for key-value lookups, kafka for events, graph database for connected data, cassandra or some other db as primary database/datastore in a same application.

## All Things Distributed

One question that always came to my mind, `How does google/amazon handle so many requests?`

I would think various things, they must have had heavy machines(hardware) running their applications, they must have written their applications in a different way. Now I know I was very wrong. There is a limit, at some point scaling vertically will be very difficult, nearly impossible. Instead of giving your application node more and more resources, you add brothers and sisters to it, which will work together to cater to the requests. This imparted the term `Horizontal Scaling` in me.

The lessons/courses I attended learning CIDRs, subnets, proxies, NATs, route tables are all useful even if I am an application developer. All these are helpful for me to realize how a request flows in and out of my application. It helps debug issues in the network itself and even importantly write better and scalable application.

Those learnings in college corridors are vital while understanding and using cloud resources. Distributed systems are real and evolving day by day. While learning dynamo/cassandra I could recall the concepts like causal ordering, vector clocks gossip and how to continue to work even after node failures etc.

## Containers
Scaling has never been easy. I got to learn more while looking for more in similar fronts, Statelessness of applications and immutability of deployments([Immutable deployments](https://www.digitalocean.com/community/tutorials/what-is-immutable-infrastructure)) can be fruitful in scaling my applications and balancing the load across the replicas of the same application.
The rapid embrace of containers has helped us realize immutability of deployments, and eased the process of shipping application. Container orchestrators like kubernetes has taken this few steps further. With kubernetes deployments become seamless with no downtime. It has certainly made scaling of applications reliable and easier.

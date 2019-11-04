---
layout: post
title:  "Microservices"
author: chandan
categories: [ microservices, monorepo]
image: assets/images/microservices.jpeg
types: [post]
published: true
---


I could have come up with a better title for this post but that’s alright since we will talk things around microservices anyway.
Wikipedia defines micro-services as - "_Microservices are a software development technique — a variant of the service-oriented architecture(SOA) architectural style that structures an application as a collection of loosely coupled services._"

Microservices with its high agility brought some side effects due to its distributed architecture. These side effects forced developers to be more conscious of the architectural model, the contracts, isolating functionalities and grouping them (functionalities that change together), ensuring that domain logic remains outside the API gateway.

If we think around microservices which states — isolated development, deployment, scaling etc. the most obvious answer to organizing code — have different repositories for different services. For small teams with relatively small domain this might work but with time this lot of microservices come up within a single domain. If we think of retail domain each subdomain like price, payment, order management etc. all of them can comprise of a lot of microservices. Generally, each of subdomains is handled by a different agile team(dev-ops teams), now how do we organize these microservices within a single team — do we have multiple repositories? or a single repository?

There are a lot of discussions and blogs written on mono repo vs multi repo. To anyone, it would seem a contentious topic. With mono-repo refactoring, issue tracking becomes much easier, on the other hand, CI/CD is a little harder. But the opposite holds for multi-repo models. Choose whatever works for you. Here in this post, I have tried to outline how I would start with a mono repository and eventually shift to more than one repo if needs be.
I watched a video that said write code that is easy to delete. It totally makes sense. But how do I write code that's easy to remove? write explicit, write small. And now we organize our repository around this and remove code out to a new repository whenever felt necessary. If we have to write software in golang and follow standard go project layout, the code structure would be like this

```
my_project/
  build/
  deployments/
  cmd/
  pkg/
  README.md
```

**pkg/**

The small, explicit code that we talked earlier has to be organized in a micro-modular way inside pkg/, so that each module implements some business logic. And we call them micro-packages. Most gophers suggest not to have a util/ package and placing requirements inside the micicro-packages itself. If we think around this, it makes each micro-package self-sustainable and more logical and thus easy removal in the future. For eg. consider having a micro-pkg called model/ inside pkg/, this gives intuition that any schema related information can be found under the micro-package model/, but it makes code removal challenging.

**cmd/**

Main applications for this project. A directory (e.g., /cmd/myservice) inside cmd/ is the application layer of a service. It should not contain any business logic, business logic should be placed inside pkg/. Services inside cmd/ import micro-packages from inside pkg/. Today, the application layer can be REST, tomorrow it can be gRPC.

It’s true that layered architectures have low agility, low ease of deployment, but having the application and domain segregation helps, makes code removal easier.

#### Mono vs Multi Repo
If we already have granular subdomains as we have in retail, we start with a repository per sub-domain, and each of them organized according to our discussion above. With time as we feel the need for more services, we add it in the same repository abiding same guidelines of cmd/ and micro-packaging inside pkg/.

Ideally, such code organization (without any other sophisticated tooling) should handle several(10 -20) microservices within a single repository building/compiling relevant micro-packages based on file changes. Even then should you feel the need to split the repository, cherry-pick the micro-packages from pkg/ and the corresponding application layer code from cmd/ and place them in the newly created separate repository.

We started the discussion with golang in mind, but the same applies to other languages as well. Write code that is explicit(one of the zens of python), simple, small and easy to delete. If writing microservices in java, organize each micro-service in two different modules — one comprising of business logic and another containing application layer code. Same goes for other languages as well.

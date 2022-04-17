---
title: "DDD in PHP Experiment"
modified: 2014-12-11
description: Domain Driven Design in PHP Experiment and Seed
tags: [ddd,php,patterns]
date: 2014-12-11T12:52:29-07:00
---

Domain-Driven Design in PHP Experiment and Project Seed

A current and difficult software development project has recently sent me scurrying for answers.  In that search I've rediscovered the book [Domain-Driven Design: Tackling Complexity in the Heart of Software](http://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/ref=sr_1_1?ie=UTF8&qid=1418357436&sr=8-1&keywords=domain+driven+design) by Eric Evans.  In addition to re-reading the book and reviewing a handful of slide-decks at [SlideShare](http://www.slideshare.net/); I have found that there a few different and even wide varying implementations of the principles of domain-driven design.  So I have started a [Github project](https://github.com/stringhamdb/d3x) to test out the implementation differences.

* First, I am looking at the differences in the persistence and database access (DBAL) components in the infrastructure layer.  
    * For example one question that needs to be answered is should a DataMapper reside in the Domain or Infrastructure layer.
    * Another is should the DataMapper be implemented following the pattern religiously or with application specific variations.
    * Is it really a DataMapper or is it better called a DomainMapper that then uses TableDataGateways and RowDataGateways to read from persistence storage?
    * Is there a DataMapper class in the infrastructure layer that communicates with the DomainMapper in the domain layer?  That these two objects can pull from multiple tables using SQL and create a single entity or a single aggregate entity.

* Second, I am looking at the differences in how domain classes versus infrastructure classes are constructed via factories.
    * Which factory pattern is a best practice?
    * If the factory method pattern is the best practice should it be implemented religiously or with variations?

* Thirdly, where can I use things like `memcached` or an op-code cache to improve the performance of large data sets.
    * Data sets such as a repository might easily grow beyond a thousand aggregate  root entities with maybe over tens times that in regular entities.
    * Large data sets could easily cause the database syndrome known as 'death by a thousand cuts' meaning that a repository during a load process could easily ask the infrastructure layer to make a lot of database calls bringing the server to it's knees.

Anyways, it should turn into a great learning experience.

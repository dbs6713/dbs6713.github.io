---
title: "Service Locator vs. Dependency Injection Container"
description: I am really not as crazy as I thought!
tags: [php,patterns]
date: 2014-12-23T22:47:30-07:00
---
I am **NOT** as crazy as I thought!

Over the last few years of learning to incorporate Java-like patterns into my PHP development practices one area seemed to drive me crazy, almost to the point of second guessing myself about [dependency injection](http://fabien.potencier.org/article/11/what-is-dependency-injection) altogether.  Years ago I learned from [Misko Hevery](http://misko.hevery.com/) from Google that a service locator is really just global state or a bad singleton in sheep's clothing.  He states that a service locator violates the [Law of Demeter](http://en.wikipedia.org/wiki/Law_of_Demeter) and calls singletons are pathological liars.  

Needless to say I have developed a bad taste for singletons and service locators.  So when I saw that many PHP projects had dependency injection containers (DIC) that were used as a service locator I became sick.  I discussed the issues with many PHP developers who didn't seem to understand the negative issues that dependency injection containers create for testing and loosely-coupling.  That is when the second guessing started.  So I did some research on the internet and found only two others that felt the way I did.  Here are their links:

* [Service Locator vs Dependency Injection Container (or Tell, Don't Ask Part 2)](http://adamcod.es/2013/11/25/service-locator-vs-dependency-injection-container.html)
* [Inversion of Control, Dependency Injection, Dependency Injection Container and Service Locator](http://gnugat.github.io/2014/01/22/ioc-di-and-service-locator.html)

Basically, in my opinion, a service locator and dependency injection container are for all intents and purposes identical.  The difference is in how they are used.  Typically, a service locator is passed into a class which then asks the locator for a dependency.  A dependency injection container is used to get the dependencies and then pass them into the class that will use them.  Essentially, this is a similar view point that Adam Brett holds.  Read his article for code examples of both a service locator and dependency injection container.

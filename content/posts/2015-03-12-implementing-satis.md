---
title: "Implementing Satis"
description: Implementing a local Packagist with Satis
tags: [php,composer]
date: 2015-03-12T09:05:00-07:00
---
Implementing a local Packagist with **Satis**

Many large companies, including the one I am currently working for [FamilySearch, Intl.](http://familysearch.org), operate many servers that do not have connectivity to the internet at large.  In other words, they cannot reach [Packagist](https://packagist.org/) rendering using [composer](https://getcomposer.org) useless.  Luckily, the developers at *composer* have provided a solution to the above problem, [private packages](https://getcomposer.org/doc/articles/handling-private-packages-with-satis.md).  I had been using *composer* for awhile but was un-aware of **Satis** or **Toran Proxy** until I attend Rafael Dohms [Composer: The Right Way](http://www.slideshare.net/rdohms/composer-the-right-way) at php[world] 2014 in Washington, D.C.  It took a couple of months of getting priorities off my plate but here is what I have learned implementing Satis for the EMS 2.x (Event Management System) for ICS.


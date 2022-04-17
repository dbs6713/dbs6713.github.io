---
title: "Optimizing the realpath_cache"
description: Better PHP performance by optimizing realpath_cache
tags: [php]
date: 2015-03-09T09:05:49-07:00
---
Better PHP performance by optimizing *realpath_cache*!

System calls are big performance hits on an OS.  Systems calls typically lead to context switches in which the CPU state is saved and retrieved during which kernal code in the CPU pipeline.  Anyways, filesystem access definitely uses system calls in an OS.  PHP does that a lot especially during *include*, *require*, *include_one* and *require_once*.  Anytime a file is accessed PHP will issue a `realpath` call.  This call asks the system for path information mainly using the the `lstat` system call.  To help improve performance `realpath` will put the returned information into a cache.

To see the data in the `realpath` cache you can use the PHP function `realpath_cache_get()` which will show you an array path information.  Even with a simple script you can get up to a dozen entries.  For small to medium sized PHP applications the defaults for the cache will be fine.  But if you are using a framework and/or builing an enterprise PHP application the cache size can quickly run out.  It is good practice to add `realpath_cache_size = 1024k` to the *php.ini* to ensure the cache is large enough to hold all the path entries.

Another issue with `realpath_cache` is that TTL (time to live) is defaulted to two minutes.  Again for a small, short running script that is fine but for a medium to large application, one that is longer running the TTL is too short.  A good practice is to add the line `realpath_cache_ttl = 360` to the *php.ini* thereby keeping the path information in the cache a lot longer.

These two additions to *php.ini* should ensure better performance in your medium to large PHP web and client applications.  
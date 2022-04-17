+++
title = "Semantic Versioning"
description = "We should all be using Semantic Versioning"
tags = ["tagging", "code"]
date = "2014-12-08T11:10:52-07:00"
+++

We should all be using [Semantic Versioning](http://semver.org/):

During this November I attended the [PHP[WORLD] 2014](http://world.phparch.com/) conference in Washington, D.C.  To say
that it was a beneficial conference would be an understatement. It seemed that valuable information was being shared at
every corner.  One of those gems is [semantic versioning](http://semver.org/).  This topic came up during a session on
how to use [PHP Composer](https://joind.in/talk/view/11878) by Rafael Dohms.

Semantic versioning uses the familiar format _xx.yy.zz_.  The _xx_'s relate to the MAJOR version and are
incremented when an incompatible API change is made.  The _yy_'s relate to the MINOR version and are incremented when
backwards compatible new functionality is added.  Finally, the _zz_'s relate to a PATCH version and are incremented for
backwards compatible bug-fixes.  So semantic versioning brings meaning to the version numbers we all see and are very
familiar with (MAJOR.MINOR.PATCH)

Why use any type of version numbering system anyways?  A question many good developers never even ask.  In my
22+ years of developing software one constant is growing dependencies.  Dependencies growth patterns are much like the
patterns followed by weeds.  They show up every and any where without rhyme or reason.  If you have ever lived in this
space you have known "dependency hell".  The sad truth is that it exists in every technology system.  In an attempt to
place some organization on the craziness of dependency growth versioning was introduced.  Quoted below is an example
of easy this can be.

> A simple example will demonstrate how Semantic Versioning can make dependency hell a thing of the past. Consider a library called "Firetruck." It requires a Semantically Versioned package named "Ladder." At the time that Firetruck is created, Ladder is at version 3.1.0. Since Firetruck uses some functionality that was first introduced in 3.1.0, you can safely specify the Ladder dependency as greater than or equal to 3.1.0 but less than 4.0.0. Now, when Ladder version 3.1.1 and 3.2.0 become available, you can release them to your package management system and know that they will be compatible with existing dependent software.

*Q:* How do I start versioning?

*A:* Start with 0.1.0

*Q:* How do I know when we are ready for 1.0.0?

*A:* Answer "yes" to these two questions, then you should be at 1.0.0.  1.) Is the software in production? 2.) Do you
have a stable API upon which users depend on.  If the you answered "no" to either question then stay with 0.x.z.

```
## EXAMPLES

 2.0.1
v2.0.0        ## 'v' is a prefix.
v2.0.0-rc.1   ## '-rc.1' is a postfix. rc=release candidate
v1.0.1-beta   ## '-beta' is a post fix.

```

Please spend some time reading through the Semantic Versioning Specification at [http://semver.org](http://semver.org).

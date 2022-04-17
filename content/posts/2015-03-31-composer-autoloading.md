---
title: "Composer Autoloading"
description: Composer Autoloading Not Just for Vendor Files
tags: [php,composer]
date: 2015-03-30T09:05:00-07:00
---
*Composer **Autoloading** Not Just for Vendor Files*

Teacher can and should learn from students!  That is one of the things I find very satisfying about being an adjunct professor at Weber State University.  The fact that I can learn new and usual things from those I teach.  Last night was one of those times.

In fielding questions about a PHP project a comment came up about multiple autoloaders.  In the first project I had the students create their own autoloader.  This project I required them to use composer to manage and load dependencies.  One student mentioned he had found how to use the composer autoloader to load his classes.  Now I had known in the past that composer supported [PSR-0](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md) but didn't fully understand it.    So to my surprise I learned that composer now supports [PSR-4](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md) and is very easy to use.  Here is a code snippet of the a portion of the `composer.json` file:

```
"autoload": {
	"psr-4": {
		"Common\\": "src/Common/",
        "Domain\\": "src/Domain/"
   }
}
```
Then to use the autoloader and namespaces in code you would use a PHP statement like this:

```php
require_once __DIR__.'/vendor/autoload.php';
```
To optimized the autoloader you can use this command: `composer dumpautoload -o`.  There is a downside to this, though.  You will need to re-run this every time a new class is added, in addition to whenever the composer `install` or `update` commands are used.  Needless to say this is a small price to pay for roughly a 40% performance increase.

This is another great usage of composer.  A tool PHP developers should be using a lot more.

* [Composer JSON Schema](https://getcomposer.org/doc/04-schema.md)
* [PHP Composer Autoloading](http://jessesnet.com/development-notes/2014/php-composer-autoloading/)
* [Optimizing Composer's autoloader performance](http://mouf-php.com/optimizing-composer-autoloader-performance)
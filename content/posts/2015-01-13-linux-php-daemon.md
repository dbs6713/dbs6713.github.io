---
title: "Linux PHP Daemon"
description: Better than a crontab!
tags: [php,linux]
date: 2015-01-13T17:50:49-07:00
---
Better than a crontab!

Many a time have my development team needed to "cronify" a PHP script for completing
business logic quietly behind the scenes.  Once the command-line (CLI) version of the
application was complete they would start creating and managing a crontab.  This
practice is **NO MORE** for my development teams!

Enter a better way of "cronifying" or better stated "daemonizing" a PHP CLI application.
I have created a sample of "daemonizing" a PHP CLI application at [https://github.com/donbstringham/php-daemon](https://github.com/donbstringham/php-daemon).
This example is based on an article by [Bobby Allen](http://blog.bobbyallen.me/2014/06/02/how-to-create-a-php-linux-daemon-service/).
Follow the directions below and now you have a linux system daemon that is actually a
PHP command-line application.

* [php-daemon.conf](https://github.com/donbstringham/php-daemon/blob/master/php-daemon.conf) - Place in the directory `/etc/init`.  On line 9 in use the **full path** to the PHP file.  It is **very** important to use *fully qualified paths* in both the [Upstart](http://upstart.ubuntu.com/) configuration file as well as any script files that [Upstart](http://upstart.ubuntu.com/) daemonizes. 
* [php-daemon.php](https://github.com/donbstringham/php-daemon/blob/master/php-daemon.php) - Place in any directory you want.  Remember it to use *fully qualified paths*.

Use the commands below to start, stop and view the status of the new linux daemon:

```
sudo status php-daemon
```

```
sudo start php-daemon
```

```
sudo stop php-daemon
```

**NOTE:** While implementing this on CENTOS/RHEL boxes a few minor changes where needed to get it run in a stable manner.  The main change was to run the daemons under the `root` user.  Other changes are listed below in the code:

##### /etc/init/php-daemon.conf

```sh
start on startup
stop on shutdown
respawn

script
    echo "DEBUG: `set`" > /root/php-daemon-env.log

    /root/php-daemon
end script
```

##### /home/stringhamdb/php-daemon

```php
#!/usr/bin/php
<?php
// The worker will execute every X seconds:
$seconds = 1;

// We work out the micro seconds ready to be used by the 'usleep' function.
$micro = $seconds * 1000000;

while (true) {
  // This is the code you want to loop during the service...
  $fh = fopen('/root/php-daemon.log', 'a') or die('Can not open file');
  $stringData = 'File updated at: '.time().PHP_EOL;
  fwrite($fh, $stringData);
  fclose($fh);
  // Now before we 'cycle' again, we'll sleep for a bit...
  usleep($micro);
}
```
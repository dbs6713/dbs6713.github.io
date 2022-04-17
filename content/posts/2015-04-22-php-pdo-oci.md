---
title: "Install Oracle PHP PDO Driver"
description: Instructions for installing Oracle PHP PDO driver on CentOS/RHEL
tags: [php, pdo, oci, oracle]
date: 2015-04-22T11:10:52-07:00
---
*Instructions for installing Oracle PHP PDO driver on CentOS/RHEL*

Download Oracle InstantClient RPM files [here](http://www.oracle.com/technetwork/topics/linuxx86-64soft-092277.html). Put these files in your server. Download the basic and devel packages.

- `Basic: oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm`
- `Devel: oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm`

Install the downloaded rpm files:

```
$ sudo rpm -ivh oracle-instantclient12.1-basic-12.1.0.2.0-1.x86_64.rpm
$ sudo rpm -ivh oracle-instantclient12.1-devel-12.1.0.2.0-1.x86_64.rpm
$ sudo ln -s /usr/include/oracle/12.1/client64 /usr/include/oracle/12.1/client
$ sudo ln -s /usr/lib/oracle/12.1/client64 /usr/lib/oracle/12.1/client
```

Create a file inside `/etc/profile.d` named `oracle.sh` and put this as the content:

```export LD_LIBRARY_PATH=/usr/lib/oracle/12.1/client64/lib```

And run it so we’ll have `LD_LIBRARY_PATH` as an environment variable.

```source /etc/profile.d/oracle.sh```

Download the PDO_OCI source using pecl.

```
$ pecl download PDO_OCI
$ tar -xvf PDO_OCI-1.0.tgz
$ cd PDO_OCI-1.0
```

Inside the PDO_OCI-1.0 folder, edit the file named `config.m4`.

Find a pattern like this near line 10 and add these 2 lines:

```
elif test -f $PDO_OCI_DIR/lib/libclntsh.$SHLIB_SUFFIX_NAME.12.1; then
  PDO_OCI_VERSION=12.1
```

Find a pattern like this near line 101 and add these lines:

```
12.1)
  PHP_ADD_LIBRARY(clntsh, 1, PDO_OCI_SHARED_LIBADD)
  ;;
```

Build and install the extension.

```
$ phpize
$ ./configure --with-pdo-oci=instantclient,/usr,12.1
$ make
$ sudo make install
```

If you see the compilation error:

```"pdo_oci.c:34: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pdo_oci_functions’"```

To solve it just change `function_entry` to `zend_function_entry` around line 34.


To enable the extension, add a file named `pdo_oci.ini` under `/etc/php.d` and put this as the content:

```
extension=pdo_oci.so
```

Validate that it was successfully installed.

```$ php -i | grep oci```

You should see something like this in the output:

```
/etc/php.d/pdo_oci.ini,
PDO drivers => oci, odbc, sqlite
```




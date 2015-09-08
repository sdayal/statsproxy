### Supported Platforms ###

The statsproxy for memcached was developed for Linux 2.6 and has been tested
on the following distributions:

CentOS 5.2 2.6.18 and later x86\_64 bit gcc 4.1.2

Linux 2.6.18-1.2798.fc6 x86\_64 gcc 3.4.6 (Red Hat 3.4.6-4)

Linux 2.6.9-1.667smp i686 athlon gcc 3.4.2 (Red Hat 3.4.2-6.fc3)

Linux 2.6.18-53.el5 x86\_64 gcc 4.1.2 (Red Hat 4.1.2-42)

Linux 2.6.12-1.1381\_FC3smp x86\_64 gcc 3.4.4 (Red Hat 3.4.4-2)

### Required Libraries ###

Requires 'bison'.

### Installation ###

Installing the statsproxy for memcached:

At your command prompt:
```
> tar -xzvf statsproxy-1.0.tgz
> cd statsproxy-1.0
> make
```
Starting the statsproxy for memcached:

At your command prompt:
```
>./statsproxy -F <config file>
```
For example:
```
>./statsproxy -F sample.cfg
```

### Configuration ###

Every memcached server that you'd like the statsproxy to monitor and report on
requires an entry in the config file.

A sample config file 'sample.cfg' is attached with the distribution.  You can
modify this file to declare the memcached servers that you wish to use
statsproxy on.

The following is the format of each memcached server entry in the config file:

For example:

To monitor a memcached server from the web running on ip mc-1 and port 11211
your proxy-mapping entry could look like following:
```
    proxy-mapping {
        front-end = "mc-1:8080";
        back-end = "mc-1:11211";
        timeout = 10;
        poll-interval = 5;
        webpage-refresh-interval = 10;
        memcache-reporter = "off";
    }
```
After you start statsproxy, point your browser to mc-1:8080 to monitor your
memcache server stats through the statsproxy web interface. You can also
use telnet to the same address to get a buffered view of stats, including
'stats health'.
```
'front-end'
IP & port information for proxied view of this memcached server

'back-end'
IP address and port for this memcached server

'poll-interval'
Defines the polling interval in seconds for the memcached server. The
statsproxy will poll the memcache service for stats on this interval.

'timeout'
statsproxy will wait this many seconds to get a stats or set response from
the memcached server.

'webpage-refresh-interval'
Webpage refresh interval in seconds.

'memcache-reporter'
Takes three different values: "modify" or "view" or "off". Reserved for
future use.
```

### Logging ###

All the logging is done to syslog.

### Usage ###

Once you have installed and configured the statsproxy for memcached, point
your browser to the server where you memcache service is running, e.g.:
```
http://frontend-ip-address:8080
```
It's that easy!

### Using Statsproxy with Cacti ###

Cacti (http://www.cacti.net/) is a popular open-source monitoring and graphing solution that uses PHP and rrdtool.  It can graph pretty much anything including memcache via templates for memcached.

Those memcache templates for cacti will also work when pointed at the statsproxy instead of the memcache instance.  A benefit to using the statsproxy is that it asks the memcache service for stats once (per configured time interval) and then can hand it out multiple times to multiple machines instead of your actual service handling those requests along with it's regular sets/gets.

To get them to work together you'd have to either modify the templates to use port 8080 or change the statsproxy config to use port 11211 (assuming your memcache server is either on a different port or IP).



## statsproxy for memcached ##

The statsproxy for memcached is a simple, but useful tool that allows you to use your web browser to get real-time stats for your memcached servers instead of or in addition to the standard memcached telnet interface.

The statsproxy for memcached provides:

  * A lightweight web view of memcached statistics without any changes or additional resource usage in memcached, i.e. stats can be easily published and viewed for your memcached servers.

  * A fast, buffered telnet view of memcached stats that can be leveraged by management and reporting systems, like Cacti.  Stats are reported in constant time irrespective of memcached's load level.

  * A synthetic 'health check' stat that is currently not available in memcached, where the statsproxy does a periodic set command and checks that the memcached server handled it correctly.

Here's a screenshot:

![http://www.mirreo.com/statsproxy_screenshot.png](http://www.mirreo.com/statsproxy_screenshot.png)

## resources ##

  * [Statsproxy support forums](http://dev.gear6.com/forums/open-source-tools-memcached/statsproxy-memcached-stats-tool)

  * [Statsproxy source at Github](http://github.com/rama/statsproxy/tree/master)
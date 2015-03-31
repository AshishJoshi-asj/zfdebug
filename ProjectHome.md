# ZFDebug has moved to [GitHub](http://github.com/jokkedk/ZFDebug) for better community support. #
**Please submit issues, patches and comments on github**


# ZFDebug - a debug bar for Zend Framework #
ZFDebug is a plugin for the Zend Framework for PHP5 written by Joakim Nygård. It provides useful debug information displayed in a small bar at the bottom of every page. ZF Debug has been renamed from **Scienta ZF Debug Bar** when moving from private hosting to googlecode. The original [page for Scienta ZF Debug Bar remains available](http://jokke.dk/software/scientadebugbar)

Time spent, memory usage and number of database queries are presented at a glance. Additionally, included files, a listing of available view variables and the complete SQL command of all queries are shown in separate panels (shown configured with 2 database adapters):

![http://jokke.dk/media/2009-scienta_debugbar.png](http://jokke.dk/media/2009-scienta_debugbar.png)

The available plugins at this point are:

  * Cache: Information on Zend\_Cache and APC.
  * Database: Full listing of SQL queries and the time for each.
  * Exception: Error handling of errors and exceptions.
  * File: Number and size of files included with complete list.
  * Html: Number of external stylesheets and javascripts. Link to validate with W3C.
  * Memory: Peak memory usage, memory usage of action controller and support for custom memory measurements.
  * Registry: Contents of Zend\_Registry
  * Time: Timing information of current request, time spent in action controller and custom timers. Also average, min and max time for requests.
  * Variables: View variables, request info and contents of $_COOKIE and $_POST

See the [installation page](http://code.google.com/p/zfdebug/wiki/Installation) for further instructions.
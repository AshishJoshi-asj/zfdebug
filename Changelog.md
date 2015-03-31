## SVN ##
New features
  * Ability to disable ZFDebug by passing ZFDEBUG\_DISABLE as GET/POST parameter
  * Works with HTML5
  * Database plugin support `EXPLAIN` on `SELECT` queries for MySQL adapters

Changed
  * Plugin icons moved to individual files
  * File plugin uses realpath on base\_path
  * Memory plugin uses dispatchLoop time in delta memory usage
  * Time plugin displays dispatchLoop time next to `$_SERVER['REQUEST_TIME']`
  * Time plugin displays average time for current request only
  * Panel widened to 800px

Fixed problems
  * Time plugin checks if the session has been started before resetting, [issue #32](https://code.google.com/p/zfdebug/issues/detail?id=#32)
  * File plugin problem with similarly named libraries, [issue #16](https://code.google.com/p/zfdebug/issues/detail?id=#16)
  * Line breaks depend on doctype setting, [issue #13](https://code.google.com/p/zfdebug/issues/detail?id=#13)

## 1.5 ##
  * Rewritten with modular plugin structure
  * Time plugin shows average/min/max request time
  * Registry plugin with contents of Zend\_Registry
  * Html plugin with basic HTML info and W3C validation
  * Memory plugin supports `mark()` method to calculate delta memory usage
  * File plugin shows total size of included files
  * Cache plugin with information on Zend\_Cache and APC
  * Debug bar remembers visibility (collapsed state) between reloads
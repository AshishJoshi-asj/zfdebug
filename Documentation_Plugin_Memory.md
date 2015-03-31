## The Memory Plugin ##

The memory plugin shows the used size of memory used to generate this script

### Options ###
None

### Contents in the menu tab ###
Used Memory in KB

### Contents in the content panel ###
Memory used during the requested controller action and any custom memory marks

### Details ###
Measure memory usage by calling the `mark()` method on the plugin like so:

```
$zfDebug = Zend_Controller_Front::getInstance()->getPlugin('ZFDebug_Controller_Plugin_Debug');
$zfMemory = $zfdebug->getPlugin('Memory');

$zfMemory->mark('Memory usage');
...
# some memory expensive operations
...
$zfMemory->mark('Memory usage');
```
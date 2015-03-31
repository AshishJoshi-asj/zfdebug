## The Time Plugin ##

The time plugin shows useful information about the different "render" steps in
your application

### Options ###
None

### Contents in the menu tab ###
  * Total time needed to render/interpret the current page/request

### Contents in the content panel ###
  * Total render time of the controller (init, specified Action)
  * Times of your own timers (see below)
  * Min/Avg/Max Time for all requests in this session

### Details ###
Set custom timers to determine specific render times of your application. This can
be very useful then optimizing your application.

```
$zfDebug = Zend_Controller_Front::getInstance()->getPlugin('ZFDebug_Controller_Plugin_Debug');
$zfTimer = $zfdebug->getPlugin('Time');

$zfTimer->mark('Slow Part');
// Lots of code
// taking very long
// to execute
$zfTimer->mark('Slow Part');
```
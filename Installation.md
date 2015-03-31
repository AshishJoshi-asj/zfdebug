# Installation & Usage #

To install, place the folder 'ZFDebug' in your library path, next to the Zend
folder.

Using the Zend\_Application component of Zend Framework 1.8+, add the following method to the Bootstrap class:

```
protected function _initZFDebug()
{
    $autoloader = Zend_Loader_Autoloader::getInstance();
    $autoloader->registerNamespace('ZFDebug');
    
    $options = array(
        'plugins' => array('Variables', 
                           'File' => array('base_path' => '/path/to/project'),
                           'Memory', 
                           'Time', 
                           'Registry', 
                           'Exception')
    );
    
    # Instantiate the database adapter and setup the plugin.
    # Alternatively just add the plugin like above and rely on the autodiscovery feature.
    if ($this->hasPluginResource('db')) {
        $this->bootstrap('db');
        $db = $this->getPluginResource('db')->getDbAdapter();
        $options['plugins']['Database']['adapter'] = $db;
    }

    # Setup the cache plugin
    if ($this->hasPluginResource('cache')) {
        $this->bootstrap('cache');
        $cache = $this-getPluginResource('cache')->getDbAdapter();
        $options['plugins']['Cache']['backend'] = $cache->getBackend();
    }

    $debug = new ZFDebug_Controller_Plugin_Debug($options);
    
    $this->bootstrap('frontController');
    $frontController = $this->getResource('frontController');
    $frontController->registerPlugin($debug);
}
```

Using older Zend Framework versions, add the following lines to your bootstrap file:

```
// Leave 'Database' options empty to rely on Zend_Db_Table default adapter

$options = array(
    // 'jquery_path' => 'http://ajax.googleapis.com/ajax/libs/jquery/1.3.2/jquery.min.js',
    'plugins' => array('Variables', 
                       'Html', 
                       'Database' => array('adapter' => array('standard' => $db)), 
                       'File' => array('base_path' => 'path/to/application/root'), 
                       'Memory', 
                       'Time', 
                       'Registry', 
                       'Cache' => array('backend' => $cache->getBackend()), 
                       'Exception')
);

$debug = new ZFDebug_Controller_Plugin_Debug($options);

$frontController = Zend_Controller_Front::getInstance();
$frontController->registerPlugin($debug);
```

The $options parameter can be either an array or an instance of `Zend_Config` with the following keys (defaults in paranthesis)

  * `z-index`: Placement on the z-axis of the html output (255, top)
  * `image_path`: Path to plugin icons (null, embedded as base64 encoded data)
  * `jquery_path`: Specify a custom path to the jQuery script. Will only be included if not already part of the page. (http://ajax.googleapis.com/ajax/libs/jquery/1.3.2/jquery.min.js)
  * `plugins`: An array of plugins to show.

It is possible to set custom timers:
```
// Get the frontcontroller and the debug bar
$frontController = Zend_Controller_Front::getInstance();
$zfDebug = $frontController->getPlugin('ZFDebug_Controller_Plugin_Debug');

// Set a custom timer
$zfTimer = $zfDebug->getPlugin('Time');
$zfTimer->mark('Query 1');
...
$zfTimer->mark('Query 1');
```
If `mark()` is called only once, the time since `$_SERVER['REQUEST_TIME']` will be shown. If invoked twice with the same name, the time between the two calls will be shown.

The same is possible with the memory plugin:

```
$zfMemory = $zfDebug->getPlugin('Memory');
$zfMemory->mark('Query 1');
...
$zfMemory->mark('Query 1');
```
If `mark()` is called once, the peak memory usage is shown. Invoked twice, the delta memory usage is printed.
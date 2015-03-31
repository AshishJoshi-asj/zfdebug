## The Database Plugin ##

The database plugin can show all queries executed to a specific database

### Options ###
There three ways to use this plugin:
  1. No Parameter: The plugin will use Zend\_Db\_Table::getDefaultAdapter
  1. Zend\_Db\_Adapter\_Abstract: If you have only one database connection
  1. An array of Zend\_Db\_Adapter\_Abstract, alternativley you can just add a second database plugin


### Contents in the menu tab ###
  * Query count and total execution time

### Contents in the content panel ###
  * Every single query with its execution time and parameters, if any

### Details ###
  * Determine any duplicate queries
  * Determine any slow queries and try to optimize them

If you use Zend\_Cache the memory plugin will allow you to see your cache enchancements.
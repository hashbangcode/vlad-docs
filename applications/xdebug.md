<h1>Xdebug</h1>

The following lines detail the options that Vlad sets as the Xdebug setup.

    xdebug.remote_enable=1
    xdebug.remote_port=9000
    xdebug.remote_handler="dbgp"
    xdebug.remote_connect_back = 1

    xdebug.profiler_enable=0
    xdebug.profiler_output_dir=/tmp/xdebug_profiles
    xdebug.profiler_enable_trigger=1
    xdebug.profiler_output_name=cachegrind.out.%p

This allows for both interactive debugging and profiling using Xdebug.

The Xdebug profiler needs to be activated by passing the XDEBUG_PROFILE variable as a GET or POST parameter. When passed during a page load this will generate a file starting with _cachegrind.out._ in the /tmp/xdebug_profiles directory. Open these files with a program like KCachegrind to see data on how your application is performing.

## Setting Up XDebug Debugger

- You must setup your host file mapping so that the local files point to the correct files on the host. This should be a setting in your IDE. The default location inside the virtual machine is /var/www/site/docroot/, so this is where the mapping should point to.
- On the host machine start your debug Listener with default settings. This should use port 9000 and the guest box IP address. The IDE Key does not matter for some IDE's, but PHPStorm likes to have a known IDE key.
- Request any page with a query string like http://www.drupal.local?XDEBUG_SESSION_START=foo. The value 'foo' does not matter - all values will cause PHP in the virtual machine to connect to the host. If you are running PHPStorm then you can create a bookmarklet that will allow you to start the debugger from any page with the correct IDE key on the following page [https://www.jetbrains.com/phpstorm/marklets/](https://www.jetbrains.com/phpstorm/marklets/).
- When your IDE receives a connection from the VM, it should prompt you to create a Path Mapping. This helps your IDE pull up an editable file instead of a read-only copy thats provided by XDebug.

## Debugging Drush Commands

If you want to use Xdebug with Drush commands, you must place drush into the docroot of the project, and set the following linux variables

export PHP_IDE_CONFIG="serverName=drupal.local"
export XDEBUG_CONFIG="idekey=PHPSTORM remote_host=192.168.100.1 remote_port=9000"

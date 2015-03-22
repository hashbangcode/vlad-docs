<h1>Variables</h1>

The following variables can be set in Vlad's [settings file](settings_file.md).

## Webserver

__webserver_hostname__

The hostname of the site you are about to create. By default this is then combined with the variable webserver_hostname_alias to add 'www' to the start.

default value: 'drupal.local'

__webserver_hostname_alias__

This is the fully qualified name of the server.

default value: 'www.{{ webserver_hostname }}'

## Vagrantfile configuration

__boxipaddress__

The IP address of the virtual machine.

default value: "192.168.100.100"

__boxname__

The name of the box that will be used by Vagrant to label the box inside your virtual machine manager of choice. This value should only contain letters, numbers, hyphens or dots. The VM will appear as `boxname` + "_vlad" in your chosen virtual machine manager.

default value: "vlad"

__vlad_os__

The OS that vlad will use. This can be one of the following:

- "centos65"
- "ubuntu12"
- "ubuntu14"

default value: "ubuntu14"

__host_synced_folder__

This is the directory that will be used to server the files from. If this doesn't exist then it will be created.

default value: "./docroot"

__aux_synced_folder__

This is a secondary Vagrant synced folder used to sync files that don't belong in `host_synced_folder`. If this doesn't exist then it will be created.

default value: "./vlad_aux"

__synced_folder_type__

Use 'nfs' or 'rsync' for VM file editing in synced folder.

default value: 'nfs'

__ansible_verbosity__

Set the level of verbosity that Ansible will use.
This can be one of "", "v", "vv", "vvv", or "vvvv".

default value: ""

__vm_cpus__

Number of CPU cores to be allocated to the guest VM from the host machine. This can be an integer or can be set to `"auto"` for Vlad to automatically assign all available cores.

default value: '2'

__vm_memory__

Amount of memory to be allocated to the guest VM from the host machine. This can be an integer (MB) or can be set to `"auto"` for Vlad to automatically assign 1/4 of host machine's memory.

default value: '1024'

__suppress_passwords__

Prevent Vlad from asking for sudo passwords when setting up the system. This can be used when the correct sudoers file is in place on the host box. This is useful when running automated tests on the system.

default value: false

## Components to install

The server components that will be installed when the box is provisioned.

- To install a component set it to true.
- To leave a component out of the install set the value to false.

__adminer_install__

Installs Adminer.

default value: true

__apache_install__

Installs Apache server.

default value: true

__imagemagick_install__

Installs Imagemagick as well as the PHP extension.

default value: false

__mailcatcher_install__

Installs Mailcatcher. Also installs the Ruby task as a dependency.

default value: false

__memcached_install__

Installs Memcache as well as the PHP extension.

default value: false

__munin_install__

Installs Munin server.

default value: false

__mysql_install__

Installs MySQL.

default value: true

__node_install__

Installs Node.

default value: false

__php_install__

Installs PHP, including a number of PHP packages as well as APC, Composer, and Xdebug.

default value: true

__pimpmylog_install__

Installs PimpMyLog.

default value: false

__redis_install__

Installs Redis.

default value: false

__ruby_install__

Installs Ruby. Ruby is required by MailCatcher.

default value: false

__sendmail_install__

Installs the Sendmail server.

default value: false

__solr_install__

Installs Tomcat 6 and Solr 4.

default value: false

__varnish_install__

Installs Varnish. Vlad will run checks to ensure that varnish can listen on port 80 and that Apache doesn't clash with that port.

default value: false

__xhprof_install__

Installs Xhprof and a Xhprof GUI.

default value: false

## Provision with custom role

__custom_provision__

Run a custom role as part of provisioning. See [Custom roles](../usage/custom_roles.md) for more information.

default value: false

## HTTP ports

__http_port__

HTTP port for the web server. If you have opted to install Varnish you will likely want to change this to `8080`.

default value: 80

__varnish_http_port__

HTTP port for the Varnish cache.

default value: 80

## Administration email

__admin_mail__

Used in instances when a server email is needed.

default value: 'test@example.com'

## PHP

__php_version__

The version of PHP to install (dependent on OS). Can be one of:

- "5.3"
- "5.4"
- "5.5"
- "5.6"

Note that Ubuntu 14 won't install < PHP5.4 so you'll get PHP5.5+. Vlad will error when a version that isn't understood is used.

default value: "5.5"

### php.ini

__php_memory_limit__

default value: 512M

__php_max_execution_time__

default value: 60

__php_post_max_size__

default value: 100M

__php_upload_max_filesize__

default value: 100M

__php_display_errors__

default value: On

__php_display_startup_errors__

default value: On

__php_html_errors__

default value: On

__php_date_timezone__

default value: Europe/London

### Install PECL uploadprogress

__php_pecl_uploadprogress__

default value: false

### PHP APC

__apc_rfc1867__

default value: '1'

__apc_shm_size__

default value: '256M'

__apc_shm_segments__

default value: '1'

__apc_num_files_hint__

default value: '0'

##  MySQL

__mysql_port__

default value: 3306

__mysql_root_password__

default value: sdfds87643y5thgfd

__server_hostname__

default value: vlad

__dbname__

default value: vladdb

__dbuser__

default value: vlad

__dbpass__

default value: wibble

### MySQL my.cnf

__mysql_max_allowed_packet__

default value: 128M

__innodb_buffer_pool_size__

default value: 64M

__innodb_file_per_table__

default value: true

__innodb_log_file_size__

default value: 64M

__mysql_character_set_server__

default value: utf8

__mysql_collation_server__

default value: utf8_general_ci

__skip_name_resolve__

default value: true

##  SSH

__ssh_port__

default value: 22

__use_host_id__

Add RSA or DSA identity from host to guest on 'vagrant up'.
Does not support identites that require a passphrase.

Options include:

- false         : don't add anything
- true          : add default files  (~/.ssh/id_rsa, ~/.ssh/id_dsa & ~/.ssh/identity)
- "[filename]"  : add a specific file e.g. /Users/username/.ssh/[filename]

default value: false

##  Varnish

__varnish_memory__

Sets the amount of memory that Varnish can use (in Megabytes).

default value: 512

## Redis

__redis_port__

Sets the port Redis should listen on.

default value: 6379

## Other settings

__drupal_solr_package__

Select which Solr module to install accepted values are 'search_api_solr' or 'apachesolr'

default value: "search_api_solr"

__hosts_file_location__

Local hosts file location.

Default location on *nix hosts is '/etc/hosts'.

Default location for GasMask on OSX is '/Users/< username >/Library/Gas Mask/Local/< file >.hst'.

default value: "/etc/hosts"

__hosts_file_update__

Select whether Vlad should edit the hosts file.

default value: true

__db_import_up__

Import MySQL database from file on 'vagrant up'.

Options include:

- false          - don't import anything
- true          - import from vlad_aux/db_io/vlad_up.sql.gz
- "[filename]" - import from vlad_aux/db_io/[filename] (supports .sql, .bz2 and .gz files)

default value: false

__add_index_file__

Add the default index.php file (useful to turn off if you are going git clone into the web root folder). Vlad will also not overwrite any existing index.php file present in the docroot location.

default value: true

## Git config user credentials

Leave these variables empty to skip this step.

__git_user_name__

Your git username.

default value: ""

__git_user_email__

Your git email address.

default value: ""

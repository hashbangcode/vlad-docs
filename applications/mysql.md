<h1>Setting up local MySQL applications</h1>

## MySQL databases

The MySQL database has a number of important settings that can be tweaked to change the setup. The most important of these is the `dbname` setting. By default, this is set to the following:

    dbname: ['vladdb']

This will generate a single database called 'vladdb' on the provisioned box. This can be increased to any number of databases by adding more items to the configuration list.

    dbname: ['vladdb', 'database2']

It should be noted that the first database in this list is always used as the default 'main' database. This database is used by Vlad when running certain automatic actions such as checking if databases have been populated with tables.

## Automatic database dumps

When you halt or destroy a VM, Vlad will attempt to automatically export all databases to files within the vlad_aux/db_io/halt_destroy directory.

## Importing databases

Database dumps can be automatically imported when the box is provisioned by using the [db_import_up](../usage/variables.md#mysql) variable. By default this action is disabled. This functionality can be re-run in isolation (on a previously provisioned VM) using the `mysql_import` [Ansible](../usage/ansible.md) tag.

## Connecting MySQL GUI apps

### Sequel Pro (OS X)

Choose connection type "SSH" and complete the connection details as follows:

**Name:** Whatever you'd like to label this connection.

**MySQL Host:** value of `boxipaddress` variable

**Username:** value of `dbuser` variable

**Password:** value of `mysql_root_password` variable

**Database:** a single value of `dbname` variable

**Port:** value of `mysql_port` variable

**SSH Host:** value of `boxipaddress` variable

**SSH User:** "vagrant"

**SSH Key:** "~/.vagrant.d/insecure_private_key" *(browse to this file by clicking the key icon)*

### MySQL Workbench

As above - the values go in the following dialog:

![Vlad MySQL Workbench Settings](img/mysql-workbench-settings.png)

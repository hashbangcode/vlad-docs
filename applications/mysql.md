<h1>Setting up local MySQL applications</h1>

Below is a list of basic guides to setting up MySQL applications on your host box to communicate with databases located in your guest VMs.

## MySQL Database Setup

The MySQL database has a number of important settings that can be tweaked to change the setup. The most important of these is the __dbname__ setting. By default, this is set to the following:

    dbname: ['vladdb']

This will generate a single database called 'vladdb' on the provisioned box. This can be increased to any number of databases by adding more items to the configuration list.

    dbname: ['vladdb', 'database2']

It should be noted that the first database in this list is always used as the default 'main' database. This database is used by Vlad when running automatic actions such as exporting or importing the database.

## Importing Your Database

When you destroy a Vlad box a trigger will automatically export the main database to a file calle vlad_destroy.sql.gz in the vlad_aux/db_io directory. This database dump can be automatically imported back into the main database when the box is started by using the _db_import_up_ variable. By default this action is turned off, but it can be turned on if needed. This can be turned on with a simple 'true' value, which will import the same file into the main database.

This value can also be set to be the name of the file in the vlad_aux/db_io directory. In this instance the default file is ignored in favour of the given filename, which is imported into the main database.

_Note_: The automatic database import won't occur if the main database currently has tables. This is in order to prevent data loss.


## Sequel Pro (OS X)

Choose connection type "SSH" and complete the connection details as follows:

**Name:** Whatever you'd like to label this connection.

**MySQL Host:** value of ```boxipaddress``` in settings file

**Username:** "root"

**Password:** value of ```mysql_root_password``` in settings file

**Database:** value of ```dbname``` in settings file *(optional)*

**Port:** value of ```mysql_port``` in settings file

**SSH Host:** value of ```boxipaddress``` in settings file

**SSH User:** "vagrant"

**SSH Key:** "~/.vagrant.d/insecure_private_key" *(browse to this file by clicking the key icon)*

## MySQL Workbench
As above - the values go in the following dialog:

![Vlad MySQL Workbench Settings](img/mysql-workbench-settings.png)

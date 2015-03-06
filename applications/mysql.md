<h1>Setting up local MySQL applications</h1>

Below is a list of basic guides to setting up MySQL applications on your host box to communicate with databases located in your guest VMs.

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

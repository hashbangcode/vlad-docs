# Windows host support

Administrator privileges are required to run vagrant commands on a Windows host.

Because of that, you will have to open a command prompt in administration mode. Good alternatives to the basic command prompt tool in Windows are [Powershell](https://support.microsoft.com/es-es/kb/968929/en-us) (pre-installed in Windows 8.1) and [Git Bash](http://git-scm.com/download/win).

## VAGRANT_HOME
If you are using a custom [VAGRANT_HOME](http://docs.vagrantup.com/v2/other/environmental-variables.html), ensure that the directory does not have a space in it. To properly set this env variable permanently, run the following command within an administration command prompt.
```shell
setx VAGRANT_HOME "c:\vagrant\home\path" /M
```

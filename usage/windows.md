# Windows host support

Vlad now supports Windows, but there are a number of additional requirements.

- Virtualbox version 4.3.12 or above is required.
- Administrator privileges are required to run vagrant commands on a Windows host.
- .NET Framework 4 or higher
- Windows Management Framework 3.0 (PowerShell 3) for versions of Windows under 8.1.
- For Windows 8.1 (probably 8 too), to get fully working Vagrant SMB share, you need to be sure your system path variable contain:
  - C:\Windows\system32 (for command 'net share')
  - C:\Windows\System32\WindowsPowerShell\v1.0 (for command 'powershell')
  - Path to Windows SSH client provided by Cygwin, MinGW or Git (ex: C:\Program Files (x86)\Git\bin)

PowerShell 3 was installed after installing Windows Management Framework 3.0 and rebooting.

Because of the requirement for administrator privileges you will have to open a command prompt in administration mode. Good alternatives to the basic command prompt tool in Windows are [Powershell](https://support.microsoft.com/es-es/kb/968929/en-us) (pre-installed in Windows 8.1) and [Git Bash](http://git-scm.com/download/win).

## VAGRANT_HOME
If you are using a custom [VAGRANT_HOME](http://docs.vagrantup.com/v2/other/environmental-variables.html), ensure that the directory does not have a space in it. To properly set this env variable permanently, run the following command within an administration command prompt.
```shell
setx VAGRANT_HOME "c:\vagrant\home\path" /M
```

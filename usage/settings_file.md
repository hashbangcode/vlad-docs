<h1>Settings file</h1>

Variables can be set in Vlad's settings file to alter how you'd like your VM to be configured. See [here](variables.md) for a full list of available variables.

### Vlad settings file location

Vlad is happy for you to store your settings in several possible locations (relative to Vlad's `Vagrantfile`):

1. vlad_guts/settings.yml
2. settings/vlad_settings.yml
3. ../settings/vlad_settings.yml

This list is in order of precedence, if Vlad finds more than one file it will prefer the file nearest the top of the list.

See [Project structure](project_structure.md) for more information about why you'd want to consider the location of your settings file.

### "Local" settings file

Vlad's settings can be further overridden via an optional, additional "local" settings file in one of several possible locations (relative to Vlad's `Vagrantfile`):

1. vlad_guts/local_settings.yml
2. settings/vlad_local_settings.yml
3. ../settings/vlad_local_settings.yml

The local settings file will always be loaded last and provides a convenient means to make adjustments to your own environment that may be out of the scope of the project itself. For example:

- boxipaddress
- git_user_email
- git_user_name
- hosts_file_location
- hosts_file_update
- host_synced_folder
- synced_folder_type
- use_host_id

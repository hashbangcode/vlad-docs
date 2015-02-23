<h1>Settings file</h1>

Variables can be set in Vlad's settings file to alter how you'd like your VM to be configured. See [here](variables.md) for a full list of available variables.

### Vlad settings file location

Vlad is happy for you to store your settings in one of 2 possible locations (relative to Vlad's `Vagrantfile`):

1. "Inner" settings file: vlad/settings.yml
2. "Outer" settings file: ../settings/vlad_settings.yml

If Vlad finds both files it will prefer the "outer" settings file.

See [Project structure](project_structure.md) for more information about why you'd want to consider the location of your settings file.

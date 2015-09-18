<h1>Custom Base Box</h1>

The following describes how to setup the Vagrant box so that it can be used instead of the normal Ubuntu/Centos boxes that get downloaded when running Vlad.

- Provision a Vlad virtual machine as per normal.
- Run `vagrant package`. This will halt the virtual machine and create a file named "package.box" in the current directory.
- Add that new box file to Vagrant's local list of available boxes by running `vagrant box add name_of_box /path/to/package.box`. You create the 'name' for the box in this step.
- You can confirm what boxes are currently available to Vagrant by running `vagrant box list`. After adding your custom box you should see that name in the list.
- If you want to use this custom box for the project you are currently running then you'll need to make sure you have deleted the existing box. Run `vagrant destroy` to destroy the current virtual machine.
- Add the variable `vlad_custom_base_box_name` to your settings file to let Vlad know that you want to use this box to set the virtual machine up with. This only needs to be the name of the box as Vagrant already knows where to find it.
```vlad_custom_base_box_name : "name_of_box"```
- Now run `vagrant up` to boot and provision your virtual machine using the custom box as a starting point. Vlad will still run the Ansible provisioning step but this will be mainly to verify the configuration.

Once you have your custom base box you can give it to other members of your team. They'll need to run the `vagrant box add name_of_box /path/to/package.box` command but once done they will have the same setup as you and will be able to start working once they have launched the box. Although the provisioning step does run when the box launches it will only verify the configuration and as such will only take a fraction of the time than a normal Vlad provisioning run takes.

Full Vagrant documentation for the `vagrant box` command can be found [here](https://docs.vagrantup.com/v2/cli/box.html).

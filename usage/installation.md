# Installation

This page talks you through installing the components needed to get up and running with Vlad.

## Prerequesites

Vlad has a number of prerequisites that need to be met before things will work correctly.

- Vagrant 1.6.4+
- If you are using VirtualBox as your virtual machine provider then you will need VirtualBox 4.3+
- If you are not on Windows, you will need to install Ansible 1.6+

Vlad has been tested as working on Linux, OS X platforms, and Windows~~, but Windows is currently unsupported~~. Vlad has been tested with the VirtualBox and VMware Fusion providers and as such other providers are currently not supported.

### Ansible

Ansible is the provisioning system that Vlad uses. 

You don't need to install if you are using Vlad on Windows.

To install Ansible in Linux or OS X, use the following commands:

    sudo easy_install pip
    sudo pip install ansible

You may have to install some prerequisite Python packages first. "pip" (a Python package manager) should install these packages automatically so you only need to run this line if the Ansible install fails.

    sudo pip install paramiko PyYAML jinja2 httplib2 markupsafe

## Installation

When you first download Vlad you will be unable to do anything with it as the system requires the use of a [settings file](settings_file.md). There is an example.settings.yml file to get you started.

Out of the box you will get the following options:

    webserver_hostname: 'drupal.local'
    webserver_hostname_aliases: 
    - 'www.drupal.local'
    #  - 'www.example.com'

    # Vagrantfile configuration

    boxipaddress: "192.168.100.100"
    boxname: "vlad"

This will create a box called "vlad_vlad" in your VirtualBox interface. If you were to change the boxname to "nosferatu" then the box name would be "nosferatu_vlad". This allows you to see at a glance what projects you have in VirtualBox that are derived from Vlad.

In order to support multiple projects, or a Drupal multi-site installation, you can add your own server aliases. These aliases will be added to your local hosts file when Vlad fires up the VMs, and removed from there upon Vlad halt. 

### Gotchas:

Note that, if you have installed the Ansible plugin separately, you may find that Vlad doesn't build correctly.

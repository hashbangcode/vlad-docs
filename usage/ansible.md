# Ansible

Ansible is an automation and provisioning tool that makes it easy to configure systems with the needed software, configuration options and even content. It is a command line tool, written in Python, that uses SSH connections to run these actions. This means that all you need to do is have a viable SSH connection to a machine and Ansible will run any actions you want to run. Ansible can either run single commands or use what is called a playbook to run several commands. Ansible playbooks are written in YAML, which makes understanding them quite easy.

## Running Ansible separately from Vagrant

During the setup process a file called host.ini will be created in the main Vlad directory. This file contains all the information Ansible needs to interact with the Vagrant box. If you want to run the Ansible playbook outside of Vagrant you can run the following command.

    ansible-playbook -i vlad/host.ini vlad/playbooks/site.yml

Tags have been included in the playbooks to allow different parts to be run individually. For example to (re)run the varnish playbook use the following command.

    ansible-playbook -i vlad/host.ini -t varnish vlad/playbooks/site.yml

To run multiple tags just use a comma separated list of tags like this:

    ansible-playbook -i vlad/host.ini -t varnish,apache2 vlad/playbooks/site.yml

Possible tags are:

- adminer
- apache2
- aptget
- drupalinstall
- drush
- local
- mailcatcher
- memcached
- munin
- mysql
- pear
- phing
- pimpmylog
- php
- redis
- sendmail
- solr
- test
- ssh
- varnish
- xdebug
- xhprof

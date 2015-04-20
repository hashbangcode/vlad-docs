<h1>Ansible</h1>

Ansible is an automation and provisioning tool that makes it easy to configure systems with the needed software, configuration options and even content. It is a command line tool, written in Python, that uses SSH connections to run these actions. This means that all you need to do is have a viable SSH connection to a machine and Ansible will run any actions you want to run. Ansible can either run single commands or use what is called a playbook to run several commands. Ansible playbooks are written in YAML, which makes understanding them quite easy.

## Running Ansible separately from Vagrant

During the setup process a file called host.ini will be created in the main Vlad directory. This file contains all the information Ansible needs to interact with the Vagrant box. If you want to run the Ansible playbook outside of Vagrant you can run the following command:

    ansible-playbook -i vlad/host.ini --private-key=~/.vagrant.d/insecure_private_key vlad/playbooks/site.yml

Tags have been included in the playbooks to allow groups of tasks to be run in isolation. For example to re-run the varnish & apache related tasks use the following command (note the `-t` option towards the end):

    ansible-playbook -i vlad/host.ini --private-key=~/.vagrant.d/insecure_private_key vlad/playbooks/site.yml -t varnish,apache

Possible tags are as follows:

    adminer,apache,apache2,aptget,bling,composer,drupal_install,drush,drush_aliases,drush_make,git,imagemagick,mailcatcher,memcached,munin,mysql,mysql_import,node,pear,phing,php,pimpmylog,python,redis,ruby,samba,sendmail,solr,ssh,test,varnish,windows,xdebug,xhprof,yum

It is also possible to use a inline inventory syntax with the ansible-playbook command. The following is the same command as above, but in this case it doesn't use the host.ini file and instead uses the inline inventory flag.

    ansible-playbook -i 192.168.100.100, --private-key=~/.vagrant.d/insecure_private_key vlad/playbooks/site.yml -t varnish,apache

<strong>NOTE</strong>: In order for the ansible-playbook command to run correctly the ansible.cfg file must be in the directory that the command is run from. This file exists in the same place as the Vagrantfile file and as such you should only run the ansible-playbook commands from that directory. It is possible to run the command from elsewhere in the Vlad directory structure, but you'll have to set a few flags that are normally taken care of by the ansible.cfg file.

## Vlad Ansible Playbook Script

The above commands can be a bit 'copy and paste' and can only be run reliably from a single directory. As a result a helper script called vlad-play.sh has been created that helps to run the ansible-playbook in a more user friendly manner. This script is located at <em>vlad/scripts/vlad-play.sh</em>. For example, assuming that you are currently working in the 'docroot' directory of Vlad you would run the script like this:

    ../vlad/scripts/vlad-play.sh

The above command would run the full Vlad Ansible playbook, but you can also supply a single argument of the tags that should be run. For example, to run the 'apache' tag.

    ../vlad/scripts/vlad-play.sh apache

You can supply more than one tag, but this must be presented to the script as a single string or it will only take the first argument in the list.

    ../vlad/scripts/vlad-play.sh 'apache,varnish'

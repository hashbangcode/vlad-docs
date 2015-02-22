# Custom Roles

Vlad can run tasks specified within an additional "custom" role defined by you. This can be used to add additional provisioning steps that are unique to a project and/or too opinionated to be contributed back upstream to the Vlad project.

A working knowledge of [Ansible playbooks](http://docs.ansible.com/playbooks.html) is required to take advantage of this feature of Vlad.

----

## Creating a custom role

### Name & location

Vlad expects the custom role to be located at the following path, relative to the root of Vlad's own codebase (e.g. relative to the Vagrantfile):

    ../vlad-custom

### File structure

Like the other roles that ship with Vlad it should follow the file structure that Ansible expects: 
[http://docs.ansible.com/playbooks_roles.html#roles](http://docs.ansible.com/playbooks_roles.html#roles)

### Tasks

Your custom role will need to contain a main tasks file at `tasks/main.yml`. Much like the roles included within Vlad, this file is the first place within your role that Ansible will look for tasks or includes to further files that may list tasks.

### Variables

All variables defined by Vlad and possibly overridden via Vlad's settings file will be available to the custom role.

Vlad will check for an optional additional settings file for use with your custom role at the following location (relative to Vlad's Vagrantfile):

    ../settings/vlad-custom-settings.yml

### Example structure

Below is a _basic_ example file structure for a custom role, including where it sits in relation to Vlad's own codebase.

```
demo-project/
├── vlad-custom/
│   └── tasks/
│   │   ├── main.yml
└── vlad/
│   ├── Vagrantfile
│   ├── vlad/
│   └── [and so on...]
└── docroot/
```

Below is a more comprehensive example file structure for a custom role, including where it sits in relation to Vlad's own codebase. This example includes role subdirectories for default variables, templates & handlers (entirely optional). This example also demonstrates where you should place any settings that you're custom may require (`vlad-custom-settings.yml`).

```
demo-project/
├── vlad-custom/
│   ├── defaults/
│   │   └── main.yml
│   ├── templates/
│   │   └── vampire.alias.drushrc.php.j2
│   ├── tasks/
│   │   ├── main.yml
│   │   ├── avoid_garlic.yml
│   │   └── suck_blood.yml
│   └── handlers/
│   │   ├── main.yml
│   │   └── check_for_sunrise.yml
├── vlad/
│   ├── Vagrantfile
│   ├── vlad/
│   └── [and so on...]
├── settings/
│   ├── vlad-settings.yml
│   └── vlad-custom-settings.yml
└── docroot/
```

## Running a custom role

### With Vagrant

Once you've created a custom role, running it as part of Vagrant's provisioning step is simply a case of setting the following value in Vlad's settings:

    custom_provision: true

The custom role will be run as part of `vlad/playbooks/site_custom.yml`, _after_ the main Ansible playbook `vlad/playbooks/site.yml`.

###  Without Vagrant

You can run the tasks in your custom role without Vagrant in the same way that you can with Vlad's main Ansible playbook. Just make sure you call the correct playbook (this command presumes that you're currently in the same directory as Vlad's Vagrantfile):

    ansible-playbook -i vlad/host.ini vlad/playbooks/site_custom.yml

Similarly, you can narrow the focus of this command to run only specific tags that you've defined within your custom role:

    ansible-playbook -i vlad/host.ini vlad/playbooks/site_custom.yml -t tag_1,tag_2

<h1>Custom Playbook</h1>

Vlad can run an additional "custom" playbook defined by you. This can be used to add additional provisioning steps (via roles if you wish) that are unique to a project and/or too opinionated to be contributed back upstream to the Vlad project. It's a great way to tune Vlad to your needs as well as take advantage of the wealth of Ansible roles available on [Ansible Galaxy](https://galaxy.ansible.com) and [GitHub](https://github.com/search?utf8=%E2%9C%93&q=where%27s+the+ansible+guff+yo%3F&type=Repositories&ref=searchresults) etc.

A working knowledge of [Ansible playbooks](http://docs.ansible.com/playbooks.html) is required to take advantage of this feature of Vlad.

## Using a custom playbook

Vlad provides the following variables to help you integrate a custom playbook as part of provisioning.

| Variable | Type | Default value | Description |
|---|---|---|---|
| `vlad_custom_play` | Boolean | false | Determines whether the custom playbook will run when Vlad provisions the VM. |
| `vlad_custom_play_path` | String  | "../vlad_custom/" | Relative path to the directory that contains the custom playbook (relative to Vlad's Vagrantfile). Note the closing backslash. |
| `vlad_custom_play_file`  | String | "provision.yml" | Name of the YAML file to run within the custom playbook (including extension). |

To start using custom playbooks just include the variable 'vlad_custom_play' in your settings file and set it to 'true'. Vlad will automatically look for the file provision.yml in the directory 'vlad_custom', located above your Vagrantfile location.

### Implementation notes

- Any custom playbook will always be run _after_ Vlad's main playbook.
- Variables set within Vlad or in any of your settings files are not automatically passed to the custom playbook (these will need to be included from within the custom playbook should you want to access them).

### Running a custom playbook without Vagrant

You can run your custom playbook without Vagrant in the same way that you can with Vlad's main playbook. Just make sure you call the correct playbook (this command presumes that you're currently in the same directory as Vlad's Vagrantfile and that you're custom playbook is located at ../vlad_custom/provision.yml):

    ansible-playbook -i vlad/host.ini --private-key=~/.vagrant.d/insecure_private_key ../vlad_custom/provision.yml

Similarly, you can narrow the focus of this command to run only specific tags that you've defined within your custom playbook:

    ansible-playbook -i vlad/host.ini --private-key=~/.vagrant.d/insecure_private_key ../vlad_custom/provision.yml -t tag_1,tag_2

<h1>Submitting Tickets</h1>

If you find a problem with Vlad then we would love to hear from you on the issue queue. Due to the dependent nature of the applications involved it really saves time if you ensure that you are up to date with the Vagrant, VirtualBox, and Ansible software. This helps to eliminate them from the list of problems.

What also really helps is if you can give us a quick snapshot of what you currently have installed. This can be done by running the following command.

    echo "VirtualBox `VBoxManage --version`"; vagrant --version; ansible --version; vagrant plugin list

This produces output similar to the following:

    VirtualBox 4.3.14r95030
    Vagrant 1.6.3
    ansible 1.8.4
      configured module search path = None
    vagrant-cachier (0.9.0)
    vagrant-login (1.0.1, system)
    vagrant-share (1.1.1, system)
    vagrant-triggers (0.4.1)

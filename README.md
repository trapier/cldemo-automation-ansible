stuff
================
stuff

Before you start
----------------
This demo requires you set up a topology as per the diagram below:

             +------------+       +------------+
             | spine01    |       | spine02    |
             |            |       |            |
             +------------+       +------------+
             swp1 |    swp2 \   / swp1    | swp2
                  |           X           |
            swp51 |   swp52 /   \ swp51   | swp52
             +------------+       +------------+
             | leaf01     |       | leaf02     |
             |            |       |            |
             +------------+       +------------+
             swp1 |                       | swp2
                  |                       |
             eth1 |                       | eth2
             +------------+       +------------+
             | server01   |       | server02   |
             |            |       |            |
             +------------+       +------------+

Additionally, an out of band management server that can SSH into the leafs and
spines via the specified hostnames is required. Setting up this topology is
outside the scope of this document.

This demo is written using Ansible 2.0. Install Ansible on the management server
before you begin. If you are using the
[Vagrant reference topology](http://github.com/cumulusnetworks/cldemo-vagrant),
this can be done by just running `apt-get install ansible`. Otherwise,
instructions for installing Ansible can be found here:
https://docs.ansible.com/ansible/intro_installation.html

Running the Demo
----------------
    git clone https://github.com/cumulusnetworks/cldemo-automation-ansible
    cd cldemo-automation-ansible
    ansible-playbook deploy-bgp.yml
    ssh server01
    ping 172.16.2.101

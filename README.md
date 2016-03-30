stuff
================
stuff

Quickstart: Run the demo
------------------------
(This assumes you are running Ansible 1.9.4 and Vagrant 1.8.4 on your host.)

    git clone https://github.com/cumulusnetworks/cldemo-vagrant
    cd cldemo-vagrant
    vagrant up oob-mgmt-server oob-mgmt-switch leaf01 leaf02 spine01 spine02 server01 server02
    vagrant ssh oob-mgmt-server
    sudo su - cumulus
    echo 'deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main' | sudo tee /etc/apt/sources.list.d/ppa_ansible.list -a
    sudo apt-get update
    sudo apt-get install ansible -qy
    git clone https://github.com/cumulusnetworks/cldemo-automation-ansible
    cd cldemo-automation-ansible
    ansible-playbook run-demo.yml
    ssh server01
    wget 172.16.2.101
    cat index.html


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

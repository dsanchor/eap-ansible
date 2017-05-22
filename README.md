# eap-ansible

This repository contains an ansible playbook to perform an basic EAP installation. This playbook will:

1. Subscribe the system using Red Hat subscription manager
2. Install java
3. Install EAP, enable the service and start it. 

This playbook DOES NOT perform any advanced EAP configuration. It will just install it.

For more information about ansible and getting started see: http://docs.ansible.com/ansible/intro_getting_started.html

#### Requirements

In order to run this playbook you need a remote user with ssh passwordless access. If other user different than root is used, this user must be sudoer.

#### Configuration

This playbook has two main configuration files:
1. [vars/identity.yml](vars/identity.yml): redhat_user and redhat_password variables for subscribing the system using Red Hat manager. If encryption for this file is needed (recommended), see http://docs.ansible.com/ansible/playbooks_vault.html
2. [vars/main.yml](vars/main.yml): optional variables for selecting different installation modes. Ex: eap_operating_mode=[standalone|domain]

#### Examples

To run a simple installation using default inventory (/etc/ansible/hosts) using defaults:

`ansible-playbook playbook.yml`

To run a simple installation providing an inventory file using defaults:

`ansible-playbook playbook.yml -i path-to-file`

To run a simple installation over one server using defaults:

`ansible-playbook playbook.yml -i 172.28.128.3,` Note: Last comma do the trick. If missing, -i provided value will be consider as a path to an inventory file

To run the playbook using a different user that root

`ansible-playbook playbook.yml -i 172.28.128.3, -u david --sudo`

To override vars

`ansible-playbook playbook.yml -i 172.28.128.3, -u david --sudo  --extra-vars "redhat_user=otheruser eap_operating_mode=domain"`





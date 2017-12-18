# Hands-On-Ansible
This repository have the goal of providing an opportunity for all the people to get an insight on how to play with Ansible.

## What is Ansible?
Ansible is an open source IT configuration management, deployment, and orchestration tool, based on Python.

## Architecture

* There are two types of machines in the Ansible architecture: the control node and managed hosts.
* Ansible software is installed on the control node and all of its components are maintained on it.
* The managed hosts are listed in a host inventory, a text file on the control node that includes a list of managed host names or IP addresses.
* Ansible uses SSH as a network transport to communicate with the managed hosts.
* The modules referenced in the playbook are copied to the managed hosts.
* Then these modules are executed, in order, with the arguments specified in the playbook.

![picture alt](https://github.com/Ompragash/Hands-On-Ansible/blob/master/images/ansible-architecture.png)

## Ansible Core Components

### 1. INVENTORIES
 
  1.An inventory is a text file listing hostnames usually grouped by functionality.









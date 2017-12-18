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
An inventory is a text file listing hostnames usually grouped by functionality. Files are organized as hosts and groups. A set of hosts can be under a group name. A host can be in more than one group.
    
**Recommendations on the Inventory**
* Give inventory nodes a human-friendly name rather than just putting the IP addresses or DNS hostnames.

### Types of Ansible Inventories:
#### 1. Static Inventory
* Static inventory is default inventory and is defined in the /etc/ansible/ansible.cfg file. 
#### 2. Dynamic Inventory
* Dynamic inventory to pull files from dynamic sources and cloud.
* If you have the setup where you add and remove the hosts very frequently, then keeping your inventory always up-to-date become a little bit problematic. In such case Dynamic inventory comes into picture.
* These are generally Python or Shell scripts for dynamic environments (for example cloud environments).

![picture alt](https://github.com/Ompragash/Hands-On-Ansible/blob/master/images/static-inventory-example.png)

### 2. Ansible Modules
* Modules control system resources like services, packages, files, system commands, etc. 
* It can be executed directly in CLI or through playbooks.
* Modules are language independent and idempotent(Avoid changes to system unless needed).
* There are three types of Ansible modules they are Core, Extras, and Custom modules
  * Core and Extras modules are always available. Ansible looks for custom modules on the control node in directories defined by the $ANSIBLE_LIBRARY environment variable.








 


        














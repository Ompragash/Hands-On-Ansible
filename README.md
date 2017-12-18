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

![picture alt](https://github.com/Ompragash/Hands-On-Ansible/blob/master/images/ansible-architecture-new.jpg)

## Ansible Core Components

### 1. Inventory
An inventory is a text file listing hostnames usually grouped by functionality. Files are organized as hosts and groups. A set of hosts can be under a group name. A host can be in more than one group.
    
**Recommendations on the Inventory**
* Give inventory nodes a human-friendly name rather than just putting the IP addresses or DNS hostnames.

### Types of Ansible Inventories:
####  1. Static Inventory
* Static inventory is default inventory and is defined in the /etc/ansible/ansible.cfg file. 
####  2. Dynamic Inventory
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
  #### Running ad hoc commands
 * To execute an ad hoc command, administrators need to execute the ansible command using the following syntax:
 
    $ *ansible host-pattern -m module [-a 'module argument']* *[-i inventory]*
  
### 3. Ansible Configuration File
* Simply Configuration file modifies the behaviour of ansible.
* When an ad hoc command is executed, First, the Ansible configuration file is consulted for various parameters.
* By default, connections to managed hosts are initiated using the SSH protocol. 
* The SSH protocol requires the connection to be established using an account on the managed host.
* This account is referred by Ansible as the remote user and is defined using the remote_user parameter under the [defaults] section of the configuration file. 

    $ *ansible node -m ping*
* The recommended practice is to create an ansible.cfg file in a directory from which  you run Ansible commands.
### 4. Ansible Playbook
* Playbooks are executed using the *ansible-playbook* command.
  * Playbook contains Plays
  * Plays contains Tasks
  * Tasks call Modules
  * Tasks run sequentially
  * Tasks triggers handlers
  * Handlers run once at the end
* Complex playbooks may contain a long list of tasks.With Ansible version 2.0, *blocks* offer another alternative to task organization.

![picture alt](https://github.com/Ompragash/Hands-On-Ansible/blob/master/images/Ansible_Playbook.png)

### 5. Ansible Variables
* Ansible supports variables that can be used to store values that can be reused throughout files in an entire Ansible project.
* Simply we can manage dynamic values in our project.
* Quotes are mandatory when we use variables is used as the first element.
* Some examples of values that variables might contain include:
  1. Users to create.
  2. Packages to install.
  3. Services to restart.
  4. Files to remove.
  5. Archives to retrieve from the Internet.
  
### 6. Ansible Facts
* Ansible facts are variables that are automatically discovered by Ansible from a managed host.
* Facts are pulled by the setup module and contain useful information stored into variables that administrators can reuse.
* Fact variables can be used as part of playbooks, in conditionals, loops, or any other dynamic statement that depends on a value for a managed host.
* We can also create custom facts and push them to a managed node.

    #### Displaying facts from a hosts:
    
    $ *ansible host-pattern -m setup*
    
### 7. Ansible Roles
* Roles provide Ansible with a way to load tasks, handlers, and variables from external files.
* Static files and templates can also be associated and referenced by a role.
* Roles can be written so they are general purpose and can be reused.
* Some basic advantages of roles:
  1. Roles group content, allowing easy sharing of code with others.
  2. Roles can be written that define the essential elements of a system type: web server, database server, git repository, or other purpose.
  3. Roles make larger projects more manageable.
  4. Roles can be developed in parallel by different administrators.
  
###  8. Ansible Galaxy
* Ansible Galaxy [https://galaxy.ansible.com] is a public library of Ansible roles written by a variety of Ansible administrators and users. 
* It is an archive that contains thousands of Ansible roles and it has a searchable database that helps Ansible users identify roles that might help   them accomplish an administrative task. 
* It includes links to documentation and videos for new Ansible users and role developers.
* Ansible-galaxy search subcommand searches Ansible Galaxy for the string specified as an argument. The --author, --platforms, and --galaxy-tags options can be used to narrow the search results.

### 9. Ansible Vault
Vault is used to protect sensitive data in your playbooks.

  * To create a new encrypted data file, run the following command:
    *  $ _ansible-vault create secret.yml_
    
Similarly we can use edit, encrypt, decrypt and rekey, for more details on how to work with vault files, check manual page:

   $ _man ansible-vault_






  
  
  
  
  
    
    


  
  

    
    








 


        














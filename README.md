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
####  a) Static Inventory
* Static inventory is default inventory and is defined in the /etc/ansible/ansible.cfg file. 
####  b) Dynamic Inventory
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

```bash
ansible host-pattern -m module [-a 'module argument'] [-i inventory]
```

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

### 5. Ansible Roles
* Roles provide Ansible with a way to load tasks, handlers, and variables from external files.
* Static files and templates can also be associated and referenced by a role.
* Roles can be written so they are general purpose and can be reused.
* Some basic advantages of roles:
  1. Roles group content, allowing easy sharing of code with others.
  2. Roles can be written that define the essential elements of a system type: web server, database server, git repository, or other purpose.
  3. Roles make larger projects more manageable.
  4. Roles can be developed in parallel by different administrators.

### 6. Ansible Tasks
* Tasks are the individual actions that Ansible performs, such as copying a file, installing a package, or restarting a service. 
* Tasks can be grouped together into playbooks or roles.

### 7. Ansible Collections
* Ansible Collections are a way of packaging and distributing collections of related Ansible content, including playbooks, roles, modules, and plugins.
* They allow for sharing and reuse of Ansible content across different projects and organizations. 
* Collections can be installed using `ansible-galaxy` and once installed, their modules can be used in playbooks like any other Ansible module.
```bash
ansible-galaxy collection install community.general
```
  
### 8. Ansible Variables
* Ansible supports variables that can be used to store values that can be reused throughout files in an entire Ansible project.
* Simply we can manage dynamic values in our project.
* Quotes are mandatory when we use variables is used as the first element.
* Some examples of values that variables might contain include:
  1. Users to create.
  2. Packages to install.
  3. Services to restart.
  4. Files to remove.
  5. Archives to retrieve from the Internet.

### 9. Ansible Template
* In Ansible, a template is a file that has placeholders, which can be filled in with specific values during the playbook execution.
* Templates allow you to create reusable configuration files, scripts, or any other text file that needs to be customized for different systems or environments.
* Templates use Jinja2, a powerful templating engine, to provide a flexible and dynamic way to generate text files. The Jinja2 syntax allows you to include logic statements, such as loops and conditional statements, as well as variables and filters.
* Some common use cases of Ansible templates include:
    * Generating configuration files
    * Managing application settings
    * Generating scripts

### 10. Ansible Facts
* Ansible facts are variables that are automatically discovered by Ansible from a managed host.
* Facts are pulled by the setup module and contain useful information stored into variables that administrators can reuse.
* Fact variables can be used as part of playbooks, in conditionals, loops, or any other dynamic statement that depends on a value for a managed host.
* We can also create custom facts and push them to a managed node.

    #### Displaying facts from a hosts:
    
```bash
ansible host-pattern -m setup
```

### 11. Ansible Handlers
* Handlers are tasks that are triggered by another task, such as restarting a service after a configuration file has been updated.
* Handlers are useful when you need to perform a specific action only when a change has been made. For example, if a configuration file is modified, you might want to restart a service that is using that configuration file.
* Handlers have a unique name and can be triggered by using the "notify" keyword in a task.

### 12. Ansible Plugins
* Plugins are used to extend Ansible's functionality, such as adding new modules, inventory sources, and connection types.
* Plugins can be of different types, such as action, connection, inventory, and lookup plugins.

### 13. Ansible Vault
* Vault is used to protect sensitive data in your playbooks.

  * To create a new encrypted data file, run the following command:
```bash
ansible-vault create secret.yml
```
    
Similarly we can use edit, encrypt, decrypt and rekey, for more details on how to work with vault files, check manual page:

```bash
man ansible-vault
```

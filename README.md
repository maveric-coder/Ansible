# Ansible
Ansible is an open source IT automation platform from Red Hat. <br>
It enables organizations to automate many IT processes usually performed manually, including provisioning, configuration management, application deployment and orchestration.
<br>It is designed for IT professionals who require it for app deployment, system integration, in-service coordination, and anything else that an IT admin or network manager routinely accomplishes. Sys admins and developers would be unable to keep up if they had to manage everything manually in today’s IT environments, which are usually too complex and often have to expand too quickly.

## How Does Ansible Work?
Ansible interacts with networks and sends little programs, known as modules, to them.<br>
These modules are utilized to complete automated tasks as systems designed to be resource models for the functioning at the desired state.<br>
Ansible runs these modules and eliminates them after they’re done. If modules weren’t available, you would have to depend on ad-hoc procedures and scripting to complete tasks. <br>Ansible’s management node is the primary node overseeing the Playbook’s implementation.

Ansible takes inventory data to determine which machines you wish to control. 
<br>It has a default inventory file, but users can customize it to manage the servers they want to. To link to servers and conduct tasks, Ansible employs the SSH protocol.

## The Relationship Between Ansible and CMS
Ansible is an automation tool specifically designed for Configuration Management System tasks. In simple terms, Ansible allows you to maintain your systems in a desired state, and to configure multiple machines quickly and consistently. The ease and flexibility provided by Ansible have made it a popular tool among IT professionals. But why Ansible?

Simplicity: Ansible uses YAML (Yet Another Markup Language), which is easy to learn and implement.
Versatility: It supports various operating systems like Linux, Windows, and macOS, and offers numerous modules and integration options to manage a broad infrastructure.
Security: With features like encryption, session management, and other security measures, Ansible ensures the safety of your infrastructure.

## Ansible Concepts
Ansible is a powerful automation tool for Configuration Management, among other things. Understanding its underlying concepts is crucial for mastering it. But how do these concepts translate to the real world? Let’s delve into these concepts and explore their practical applications, which will help you grasp how Ansible fits into the bigger picture of system and network management.

### Users
Users in Ansible typically refer to system administrators, DevOps engineers, or any personnel who write and execute Ansible playbooks. These are the individuals who interact directly with the Ansible control node. In a large organization, system administrators and DevOps engineers use Ansible to automate repetitive tasks, freeing up their time for more complex responsibilities.

### Ansible Playbooks
Playbooks are YAML files that define what Ansible does when it interacts with a managed node. They are the recipes that contain tasks to be executed on managed nodes. Playbooks are easy to write, read, and understand. An e-commerce company might use playbooks to automatically scale their infrastructure up or down based on the website traffic. Here’s a simple YAML example of an Ansible playbook that installs the Apache web server:

```yml
---
- hosts: web_servers
  tasks:
    - name: Install Apache
      apt:
        name: apache2
        state: present
```
### API (Application Programming Interface)
Ansible’s API enables integration with other software and services. This is useful for advanced automation scenarios where Ansible needs to work in conjunction with other tools or databases. A cloud service provider could use Ansible’s API to integrate it into their existing service offerings, providing end-users with automated, self-service options.

### Modules
Modules are units of code that Ansible executes. Each module provides a specific piece of functionality, like installing a package or creating a file. Ansible has hundreds of built-in modules but you can also write custom ones. IT teams in financial institutions use specific modules to enforce security standards across thousands of servers. Example of using the copy module to copy a file:

```yml
tasks:
  - name: Copy file
    copy:
      src: /source/file
      dest: /destination/file
```
### Inventory
The inventory is a list of nodes that Ansible manages. This can be a static file or dynamically generated from a source like a CMDB. In a multi-cloud environment, dynamic inventories enable organizations to manage resources across different cloud providers seamlessly. Example of a simple static inventory file:

[web_servers]
192.168.1.10
192.168.1.11
Plugins
Plugins augment Ansible’s functionality. They can execute additional tasks, manipulate data, or interact with external services. Examples include inventory plugins, filter plugins, and callback plugins. In a DevSecOps pipeline, plugins could be used to insert security checks at various points in the development process.

### Hosts
Hosts are the specific machines that Ansible manages. They are defined in the inventory and can be grouped based on functionality, location, or any other criteria. In a global enterprise, hosts could be grouped by geographical location, making it easier to apply location-specific configurations or updates.

### Networking
Ansible can manage network devices from various vendors. It has specific modules designed to interact with networking hardware and software. Internet Service Providers (ISPs) might use Ansible to manage the configurations of their routers and switches across different data centres.

### Public/Private Cloud
Ansible can manage cloud resources as well. There are modules for interacting with popular cloud providers like AWS, Azure, and Google Cloud. Startups to large enterprises use Ansible to automate the provisioning and management of cloud resources, effectively managing their operational costs.

### CMDB (Configuration Management Database)
CMDBs can serve as dynamic inventory sources for Ansible, providing real-time data about the configuration items in the infrastructure. Healthcare organizations may use CMDBs as dynamic inventories to ensure that all systems are compliant with healthcare regulations.

### Control Node
The machine where Ansible is installed and from which tasks and playbooks are executed. In a multi-site retail business, the control node could be a centralized server located in the head office. From this node, IT managers can roll out updates or security patches to point-of-sale systems across all retail locations.

### Managed Nodes
These are the servers managed by the Ansible control node and serve as the target hosts where Ansible modules are executed. In a cloud-native organization, managed nodes could be dynamically provisioned as virtual machines or containers. Ansible can be used to automatically configure these nodes as they come online, ensuring they meet the company’s security and performance standards.

### Tasks
Tasks are the smallest unit of action in Ansible. They are executed sequentially and can invoke Ansible modules to perform specific actions. In a digital marketing agency, tasks in a playbook might include pulling the latest code from a Git repository, running tests, and then deploying a website to a production server. These tasks can be executed automatically every time there is a new code commit, ensuring that the client’s website is always up-to-date. Example of a task to install a package:

```yml
tasks:
  - name: Install package
    apt:
      name: some_package
      state: present
```















# Ansible test file

trying ansible


for user_site.yml
cat /etc/passwd
sudo cat /etc/shadow
ssh -i ~/.ssh/ansible yaay@10.0.0.5
whoami
try to perform some sudo privelage commands
cat .ssh/authorized_key

edit the config file and add
remote_user = yaay


after that run the playbook directly
ansible-playbook user_site.yml

copy the user_site.yml to bootstrap.yml and remove the user part from user_site and remove all other plays from bootstrap.yml

remove update_only: and upgrade: from user_site.yml
and add changed_when: false on same level as when

### for roles:
1. copy the existing playbook for backup
2. define all the reoles in the user_site.yml playbook
3. create a directory named roles and create sub-directories for each roles
4. make new directory named tasks inside each directories inside roles
5. now switch to tasks dir inside base directory and create main.yml aka taskbook
6. copy the default_site.html from root file dir to roles/web_servers/files dir


### Host variables and Handlers
1. create a new dir host_vars
2. create host variable file node1@10.0.0.5.yml ...


### template 
1. /etc/ssh/sshd_config - default apth for ssh
2. copy this file to roles/base/tasks
3. create template folder and copy the file inside this folder
4. .j2 jinja2 format for templates in ansible
5. scp node3@10.0.0.7:/etc/ssh/sshd_config sshd_config_RedHad.j2
6. AllowUsers {{ ssh_users }} add this line in the copied files
[node3@node3 ~]$ sudo chmod a+r /etc/ssh/sshd_config 
[node3@node3 ~]$ sudo chmod o-r /etc/ssh/sshd_config 

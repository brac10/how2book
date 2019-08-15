---
# Ansible Commands
---

## Mapping Devices

Use the following command to map IP to MAC addresses

- sudo nmap -sP 192.168.1.1/24 >network.txt 2>&1

The file contains MAC - Manufacturing information in a report form.

## Once Installed - Configure Ansible Hosts & Groups (This is performed on your host computer)

\$sudo nano /etc/ansible/hosts

Groups:
webservers
ubuntu_servers
database
![images](./images/image1.png)

Variables:
Allows grouping for a single
ssh_user account.

    dramble:children
    ubuntu:children

![images](./images/image2.png)

## Testing / Verfication of Ansible Setup

Your Ansible setup is ready for testing. To test all hosts connectivity using ping module like:
![images](./images/image3.png)

- \$ansible -m ping all (Verifies connectivity to all devices)
- \$ansible -m ping webservers (Verificaton by device classification where webservers has been classified as a group of devices)
- \$ansible -m ping 192.168.1.226 (allows to test one address)

## Using the Shell Module

![images](./images/image4.png)

You can also run a command using shell module. For example, test the free memory on all servers or one. You can also perform the same task for a group. Just use group name instead of hostname.

- \$ ansible -m shell -a 'free -m' all

## External Inventory Files

![images](./images/image5.png)

Allows your inventory to be placed in a file called Inventory.ini and run via ansible command or playbook.

# Ansible Galaxy

Service to download unqique roles within Ansisble.

nginx installation

- ansible-galaxy install geerlingguy.nginx

loadbalancer using nginx

- ansible-galaxy install holms.balancer

![images](./images/image7.png)

## Listing Your Installed Roles

You can use the ansible-galaxy list command to list all the roles and role versions you have installed.

- ansible-galaxy list

## Installing Multiple Roles From a File

Multiple roles can be installed by listing them in a requirements.yml file. The format of the file is YAML, and the file extension must be either .yml or .yaml.

Use the following command to install roles included in requirements.yml:

- \$ ansible-galaxy install -r requirements.yml

## Dependencies

Roles can be dependent on roles, and when a role is installed, any dependencies are automatically installed as well.

Dependencies are listed in a role’s meta/main.yml file, using the top-level dependencies keyword. The following shows an example meta/main.yml file with dependent roles:

---

dependencies:

- brac10.java

galaxy_info:
author: brac10
description: Elasticsearch for Linux.
company: "Bracom ITG"
license: "license (BSD, MIT)"
min_ansible_version: 2.4
platforms:

- name: EL
  versions:
  - all
- name: Debian
  versions:
  - all
- name: Ubuntu
  versions:
  - all
    galaxy_tags:
  - web
  - system
  - monitoring
  - logging
  - lucene
  - elk
  - elasticsearch

## Collection Metadata

Collections require a galaxy.yml at the root level of the collection. This file contains all of the metadata that Galaxy and Mazer need in order to package and import a collection.

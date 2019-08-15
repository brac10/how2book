---
# Ansible Commands 
---

## Step 1: Once Installed - Configure Ansible Hosts & Groups (This is performed on your host computer)

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

## Step 2: Test Ansible Setup

Your Ansible setup is ready for testing. To test all hosts connectivity using ping module like:
![images](./images/image3.png)

- \$ansible -m ping all (Verifies connectivity to all devices)
- \$ansible -m ping webservers (Verificaton by device classification where webservers has been classified as a group of devices)
- \$ansible -m ping 192.168.1.226 (allows to test one address)

## Step 3: Verification of Shell Module

![images](./images/image4.png)

You can also run a command using shell module. For example, test the free memory on all servers or one. You can also perform the same task for a group. Just use group name instead of hostname.

- \$ ansible -m shell -a 'free -m' all

## Using External Inventory Files

![images](./images/image5.png)

Allows your inventory to be placed in a file called Inventory.ini and run via ansible command or playbook.

## NGINX Playbook

![images](./images/image6.png)

In addition to basic installation of nginx, a template can be used to define attributes unique to the application via:

    default.conf

For each specialty server, a unique role is established for tasks within a playbook.

That allows the playbook contain the minimum values in its file with values for handlers, tasks and templates needed.

![images](./images/image7.png)


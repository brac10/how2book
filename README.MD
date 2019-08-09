<p align="center">
<h1 align="center">
 🇺🇸 Ranger-Pi How 2 Book 🇺🇸
</h1>
</p>

# 🚀 AWS (Amazon Web Services)

## Web Services

## CLI Commands

# Raspberry PI

All things related to hardware and software installation

# SD Card

# Software Installation

## Visual code

## 1. wget https://packagecloud.io/headmelted/codebuilds/gpgkey -O - | sudo apt-key add -

## 2. curl -L https://code.headmelted.com/installers/apt.sh | sudo bash

If version 1.32 is installed, you'll have to us the previous version. (29)

## 3. sudo apt-get install code-oss=1.29.0-1539702286

This will overlay the bad version. (v32)

## 4. sudo apt-mark hold code-oss

(Run this command to tell the Raspberry PI not to upgrade code-oss when other software is being upgraded as well)

# Installation of Ansible Control Machine plus all Servers

## Hardware Overview:

- Control Machine: MAC
- Real Servers: (2) Ubuntu 19.01
- 9-Raspberry Pi 3b/4B: Debian Linux (Buster)

## Installation:

### Step 1: Configure SSH Access on Control Machine:

You can configure key based ssh for the remote Linux Ansible hosts. So password will not be required for SSH. Ansible also allows you to use a password for ssh, but key-based ssh is more secure.

- \$ssh-keygen
  (you will be prompted with key-name / pass-phrase)

- key: id_rsa.pub
- passphrase: leave blank

### Step 2: Copy the public key to all of your remote devices needing connectivity

- \$ssh-copy-id -i ~/.ssh/id_rsa.pub pi@xxx.xxx.xxx.xxxx

### Step 3: Install Ansible on Ubuntu Servers 19.0X

## Ansible provides its official PPA for the installation on Ubuntu systems. Run the following command to configure Ansible PPA to your Ubuntu 18.04 system.

- \$sudo apt-add-repository ppa:ansible/ansible

### Step 4: After adding the Ansible repository execute below commands to install.

- \$sudo apt update
- \$sudo apt install ansible

### Step 5: Install Ansible on Raspberry Pi

- \$ sudo apt update
- \$ sudo pip install ansible (using Python PIP) can also use Home-brew.

# 🚀 GIT Commands / Flows

## Initialize a local repo: (after creating shell in github)

"MVP for deploying code"

- git init
- git add .
- git remote add origin https://github.com/brac10/XXXXXXX.git
- git push -u origin master

## Checkout a Branch (process used to start a project from a code base)

- git checkout -b &lt;feature branch&gt;

## apply changes

- git add .
- git commit -m "#comment:story link"

## push changes upstream from local Machine

- git push –set-upstream origin &lt;feature branch&gt;

# Software Installation

## Installing Visual Code

- wget https://packagecloud.io/headmelted/codebuilds/gpgkey -O - | sudo apt-key add -
- curl -L https://code.headmelted.com/installers/apt.sh | sudo bash

If version 1.32 is installed, you'll have to us the previous version. (29)

- sudo apt-get install code-oss=1.29.0-1539702286 
This will overlay the bad version. (v32)

### Put the code on hold

- sudo apt-mark hold code-oss
     (Run this command to tell the Raspberry PI not to upgrade code-oss when other software is being upgraded as well)

### Installation of Ansible on Control Machine / Servers

## Hardware Overview:

- Control Machine: MAC
- Real Servers: (2) Ubuntu 19.01
- (9 / Raspberry Pi 3b/4B: Debian
  Linux (Buster) ## Installation:

### Step 1: Configure SSH Access on Control

Machine: You can configure key based ssh for the remote Linux Ansible hosts. So password will not be required for SSH. Ansible also allows you to use a password for ssh, but key-based ssh is more secure.

- \$ssh-keygen (you will be prompted with key-name / pass-phrase)
- key: id_rsa.pub - passphrase: leave blank ###

### Step 2: Copy the public key to all of your remote devices needing connectivity

- \$ssh-copy-id -i ~/.ssh/id_rsa.pub pi@xxx.xxx.xxx.xxxx

### Step 3: Install Ansible on Ubuntu Servers 19.0X

Ansible provides its official PPA for the
installation on Ubuntu systems. Run the following command to configure AnsiblePPA to your Ubuntu 18.04 system.

- \$sudo apt-add-repository ppa:ansible/ansible

### Step 4: After adding the Ansible repository execute below commands to install.

- \$sudo apt update - \$sudo apt install ansible

### Step 5: Install Ansible on Raspberry Pi

- \$ sudo apt update
- \$ sudo pip install ansible

(using Python PIP) can also use Home-brew.

<<<<<<< refs/remotes/origin/master
=======
## Installing SAMBA "File Sharing"

- sudo apt-get update
- sudo apt-get install samba samba-common-bin smbclient cifs-utils
- sudo nano /etc/samba/smb.conf (remove existing content)
- replace with the following text
  <hr>
  Configuration:
  [global]
  netbios name = <b>XXXXX</b>
  server string = The Pi File Center
  workgroup = WORKGROUP
  hosts allow =
  socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
  remote announce =
  remote browse sync =

[HOME]
path = /home/
comment = No comment
browsable = yes
read only = no
valid users =
writable = yes
guest ok = yes
public = yes
create mask = 0777
directory mask = 0777
force user = root
force create mode = 0777
force directory mode = 0777
hosts allow =

<hr>

- Creating Samba User:
  -- sudo smbpasswd -a pi
  -- type password, press enter

* Restart Samba Service:
  -- sudo service smbd restart

### How to Fix VNC Server "Cannot show desktop"

- sudo apt-get install tightvncserver
- tightvncserver :1
  <p>Prompts for a password for viewing, reply 'N'</p>
- when connecting with VNCViewer, reply with IP-Address + ':1'


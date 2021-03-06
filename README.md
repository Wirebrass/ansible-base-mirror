# ansible-base

## Introduction

This document describes how to use ansible-base to deploy basic infrastructures.

The main parts of this document are:

* Ansible "server" (or local machine) preparation
* Nodes preparation
* Deployment

## Ansible "server" (or local machine) preparation

Update and install Ansible and GIT on your system.

Clone this repo (ssh pubkey needs to be authorized for this repo) and go into the cloned directory:

```bash
git clone https://git.grifon.fr/nemo/ansible-base.git
cd ansible-core
```

Download roles dependecies (currenty not used):

```ansible-galaxy install -r requirements.yml -p ./roles/```

Copy the template inventory folder and edit all subfiles to add your node(s) and other informations:

```bash
cp -R inventory_template inventory_yourInventoryName
```

> Note: you can create a dedicated private GIT repository to manage your inventory.

The main inventory file is: `inventory_yourInventoryName/inventory.yml`

Example with template values:

```bash
all:
  vars:
    ansible_user: ansible
    ansible_become: yes
    ansible_python_interpreter: auto_silent
  children:
    function:
      children:
        backup_server:
          hosts:
            mySecondGentooHost.example.org:
        munin_server:
          hosts:
            myFirstGentooHost.example.org:
        ldap_server:
          hosts:
            myFirstGentooHost.example.org:
	    ...
	...
    os:
      children:
        os_gentoo:
          hosts:
            myFirstGentooHost.example.org:
            mySecondGentooHost.anotherexample.org:
            ...
        os_debian:
          hosts:
            myFirstDebianHost.example.org:
            mySecondDebianHost.anotherexample.org:
	    ...
        os_centos:
          hosts:
            myFirstCentOSHost.example.org:
            mySecondCentOSHost.anotherexample.org:
            ...
        ...
```

> Note: the node's name needs to be reachable, you can use IP address or FQDN (recommended).

Create a vault file for all nodes using the vault template file and define all values:

```bash
cp inventory_yourInventoryName/group_vars/all/vault.yml.template inventory_yourInventoryName/group_vars/all/vault.yml
vim inventory_yourInventoryName/group_vars/all/vault.yml
```

Encrypt the vault file and check if edit function works. A prompt will ask you a password:

```bash
ansible-vault encrypt inventory_yourInventoryName/group_vars/all/vault.yml
ansible-vault edit inventory_yourInventoryName/group_vars/all/vault.yml
```

> Note: if you version your code, don't forget to exclude this vault file of versionning (with .`gitignore file` if you are using GIT).

According to your needs, you can edit all variables in `inventory_yourInventoryName` directory and subdirectories.

You can also define host-specific variables (reboot/upgrade enable/disabe, cron hours, specific config, ...) in the `inventory_yourInventoryName/host_vars` directory (host.example.org is an example). Don't forget to update .gitignore if you don't want to publish some host vars.

## Nodes preparation

On the node, with the root account (or sudo):

* Install SSH, sudo and gentoolkit (if Gentoo) OR python-apt (if Debian) OR python-yum (if CentOS) ...
* Configure, enable and start SSH service.
* Configure the ansible user :

```bash
# Create an ansible user
useradd -m -s /bin/bash ansible

# Add sudoers rights to ansible user
echo "ansible ALL=(ALL:ALL) NOPASSWD: ALL
" >  /etc/sudoers.d/ansible

# Check the sudo configuration
su - ansible
sudo -i # If OK, you're root here
exit
exit

# Add SSH public key of the account used on the Ansible server (or local machine) to the ansible user on the remote node to deploy
su - ansible
mkdir -p .ssh
vi .ssh/authorized_keys # Here add pubkey
```

> Note: this procedure can vary slightly if you're not using a Debian or  CentOS node.

On the Ansible server (or local machine), check the SSH connection:

```bash
ssh ansible@<YOUR_MANAGED_NODE>
exit
```

## Deployment

From the Ansible server (or your local machine), you can deploy specific playbooks using the following command:

```bash
ansible-playbook -i inventory_yourInventoryName/inventory.yml <playbook_name> --ask-vault-pass
```

> Notes:
>
> * `--diff` option can be added to see the difference applied.
> * `--check` option can be added to test the deployment without really do any action on the remote node (in some cases it fails even if the deployment will go well).
> * `--limit` option can be added to select host to configure (ex: `--limit os_gentoo`)

Playbook deployment:

* `playbook_general_deploy.yml`
* `playbook_backup_deploy.yml`
* `playbook_munin_deploy.yml`
* `playbook_ldap_deploy.yml`

### playbook_general_deploy.yml

This playbook deploys general configuration: tools (useful packages), auto reboot, auto upgrade, sudo users, NTP client, iptables config  and DNS resolvers.

### playbook_backup_deploy.yml

This playbook deploys a backup server with a dedicated user to save GIT repositories to backup (use Ansible vars to list them). Furthermore, it configures users for each server to backup and configure "client" servers to send backups through SSH (pubkey authent).

### playbook_munin_deploy.yml

This playbook deploys a Munin server and Munin "clients" using async to get information from "clients". He integrates HTTPS configuration and configuration generation with Ansible vars.

### playbook_ldap_deploy.yml

This playbook deploys and configures an OpenLDAP server.

### playbook_icinga2_deploy.yml

This playbook deploys and configures an Icinga2/MariaDB/Icingaweb2 server. 


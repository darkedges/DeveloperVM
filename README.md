# Development VM

Creates an initial Common Development Environment and install the following in a Centos 7 Virtual Machine.

* Ansible
* Packer
* Docker
* Gradle / Ant via SDKMan
* nvm and nodejs
* Android SDK

## Pre-Requisites

1. It relies on there being a directory `c:\development` being created for use
   as a shared folder.

1. Depends on `Vagrant`, `Ansible` and `Virtual Box` installed.
   Documentation on how to do this to follow.

## Create

    vagrant up --no-provision
    ansible-galaxy install -r ansible/development-galaxy.yml
    ansible-playbook -i ansible/inventory ansible/development-playbook.yml
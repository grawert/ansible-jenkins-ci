# Setup Jenkins CI environment with Ansible

Ansible playbooks to configure Jenkins CI with Jenkins master
and slave node with diskimage-builder environment.

Authentication is done with Apache and mod_ldap
using local OpenLDAP server.

## Requirements

- Vagrant (optional)
- Ansible 2.x

## Setup

Install external roles:

    ansible-galaxy install -r requirements.yml

Deploy:

    vagrant up

Login:

    https://192.168.11.10/
    username: alice
    password: secret


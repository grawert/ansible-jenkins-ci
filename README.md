# Setup Jenkins CI environment with Ansible

Ansible playbooks to configure Jenkins CI with Jenkins master
and slave node with diskimage-builder environment.

Authentication is done with Apache and mod_ldap using OpenLDAP server.

## Requirements

- Vagrant (optional)
- Ansible 2.x

## Setup

Install external roles:

    ansible-galaxy install -r requirements.yml

Credentials:

See configuration in *group_vars/jenkins_master at *password_credentials*
and *ssh_credentials*.

The following files are expected:

    credentials/
    |- imgbuild_ssh_key.pem
    `- jenkins_ssh_key.pem

The following environment variables for an Openstack user are expected:

    OS_USERNAME
    OS_PASSWORD

Deploy:

    vagrant up

Login:

    https://192.168.11.10/
    username: alice
    password: secret

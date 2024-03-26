# GlassFish 3.1.2.2 Ansible Role
## Overview
This Ansible role automates the deployment and basic configuration of GlassFish Server 3.1.2.2. It handles the installation, sets up domains, configures JVM options, create Clusters and Instances with Properties and manages JDBC resources.

## Requirements
- Ansible 2.9 or later.
- Target servers should be UNIX/Linux with SSH access.

## Features
- Installs GlassFish 3.1.2.2.
- Configures GlassFish domains, clusters, instances and system-properties.
- Manages JDBC connection pools and resources.
- Sets JVM options for performance tuning.

## Tested Environments
This Ansible role has been tested successfully on the following operating systems:

- Ubuntu 22
- Red Hat 8

## Quickstart Guide

1. **Inventory Setup**: Define your hosts in the Ansible inventory.
2. **Role Configuration**: Customize variables in `vars/{{ inventory_hostname }}.yml` to fit your environment.

3. **Execute Playbook**: 

Before executing the playbook, please consider the following:

- Ensure you have uploaded the compressed JDK Java file in ZIP format into the roles/files directory.
- Modify the value of `java_version` in the environment variables located in roles/vars/{{ inventory_hostname}}. 
Make sure it matches the name of the compressed JDK Java file you uploaded in the previous step. For example:

```bash
# Modify according to the name of the uploaded Java JDK in files/
java_version: "jdk1.8.0_144"
```

- Run your playbook including this role:
```bash
ansible-playbook -i inventory/your_inventory.yml your_playbook.yml --tags <install,create,gf_uninstall>
```

### Tag definition

- install: 
    - Glassfish 3.1.2.2 install.
    - Java JDK 8 default install.
- create:
    - create user with GID and UID in `vars/{{ inventory_hostname }}`
    - create cluster, instance, jdbc connection pool, jdbc resource, system-properties
- uninstall:
    - uninstall glassfish and java (delete /GLASSFISH_HOME)

## Security
- Ensure you use secure passwords and manage credentials safely.


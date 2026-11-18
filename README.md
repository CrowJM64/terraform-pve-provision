# WORK IN PROGRESS ROLE
# Ansible Role for SSHD Hardening
**Author/Maintainer:** Josh Murphy

## Overview

This Ansible role provisions a Terraform user on a Proxmox host with all the relevant PVE Realm access and SUDO permissions for disk importing.

## Requirements
------------

This role must be applied to a Proxmox host, on PVE verion 8 or above.

## Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

## Dependencies
------------
```yaml
- ansible.community.proxmox
```

## Example Playbook

```yaml
- hosts: all
  become: yes
  roles:
    - role: terraform-pve-provision
```

License
-------

MIT

### From Ansible Galaxy

```bash
ansible-galaxy install crowjm64.headscale-install
```

This role was created and is maintained by **[CrowJM64](https://github.com/CrowJM64)**.
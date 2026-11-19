# WORK IN PROGRESS ROLE
# Ansible Role for SSHD Hardening
**Author/Maintainer:** Josh Murphy

## Overview

This Ansible role provisions a Terraform user on a Proxmox host with all the relevant PVE Realm access and SUDO permissions for disk importing using qm and pvesm.

A Proxmox API access token will be created, and saved to /root/ which can then be used to access the node via Terraform, along with the SSH PubKey and Password set in the role variables. (SSH and scoped sudo is required to import disk images to the ProxMox node.)

## Requirements

This role must be applied to a Proxmox host, on PVE verion 8 or above on which the following are true:
- Sudo is installed.
- The ansible user has the rights to become root.

## Role Variables

```yaml
terraform_user: # PAM Username for the Terraform user.
terraform_group: # PAM Groupname for the Terraform user.
terraform_user_password: # Reccomended to set this in the relevant Ansible Vault. This is the password that the Terraform user will later use to authenticate to the Proxmox node. (Assuming PubKey authentication has not been configured on the Proxmox Node.)
terraform_user_email: # Email to be associated with the Terraform User on the Proxmox node.
terraform_pve_role: # Name of the role created within the Proxmox PVE Realm
terraform_ssh_key: # Reccomended to set this in the relevant Ansible Vault. This is the SSH PubKey that the Terraform user will later use to authenticate to the Proxmox node. (Assuming PubKey authentication has been configured on the Proxmox Node.)
terraform_token_name: # Desired name for the Token the Terraform user will use.
```

## Dependencies

```yaml
N/A
```

## Example Playbook

```yaml
- hosts: all
  become: yes
  roles:
    - role: terraform-pve-provision
```

## License

MIT

### From Ansible Galaxy

```bash
ansible-galaxy install crowjm64.terraform_pve_provision
```

This role was created and is maintained by **[CrowJM64](https://github.com/CrowJM64)**.
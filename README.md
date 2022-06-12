# ansible-ubuntu-kvm
Ansible role to configure KVM hypervison on linux (Ubuntu) server 

## Description

Role performs KVM installation and configuration:
 - Install KVM and related packaged
 - Disable SELinux for libvirt
 - Add users who will manage KVM
 - Configure storage pools
   - default (<kvm_data_folder>/img)
   - iso (<kvm_data_folder>/iso)
 - Configure networks
   - default (virbr0 interface)
   - external (br0 inferface, if exists)

## Installation

Create requirements.yml file

```
# Include ubuntu-kvm role
- src: https://github.com/FastMT/ansible-ubuntu-kvm.git
  name: ubuntu-kvm
  version: "v1.0.0"
```

Install external module into ~/.ansible/roles folder

```
ansible-galaxy install -r requirements.yml
```

## Usage

playbook.yml:

```
# Configure iptables
- role: "ubuntu-kvm"
    vars:    
      # Optional parameter - VM base folder (default: "/vm")
      kvm_data_folder: "/vm"

      # Optional parameter - users who have rights to manage libvirt
      kvm_users:
        - { user: "user1" }

```        
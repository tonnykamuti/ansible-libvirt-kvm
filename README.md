# Using Ansible to automate/manage  libvirt/KVM infrastructure

## Overview

Shows progressive approach using ansible's community.libvirt collection to manage virtual machines, networks and pools
```bash
tonny@xor:~/Documents/projects/ansible/libvirtsetup$ ansible-doc --list community.libvirt
community.libvirt.virt      Manages virtual machines supported by libvirt
community.libvirt.virt_net  Manage libvirt network configuration
community.libvirt.virt_pool Manage libvirt storage pools
tonny@xor:~/Documents/projects/ansible/libvirtsetup$

```

## Setup
Here is the infrastructure:

A desktop (xor) with ansible installed locally
```bash
tonny@xor:~/Documents/projects/ansible/libvirtsetup$ ansible --version
ansible [core 2.16.3]
  config file = None
  configured module search path = ['/home/tonny/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /home/tonny/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible
  python version = 3.12.3 (main, Aug 14 2025, 17:47:21) [GCC 13.3.0] (/usr/bin/python3)
  jinja version = 3.1.2
  libyaml = True
tonny@xor:~/Documents/projects/ansible/libvirtsetup$
```

Two KVM hosts with libvirt/kvm installed already:

 kvm1.tkk.internal - Ubuntu 24.04.2 LTS (GNU/Linux 6.8.0-136-generic x86_64) - 8GB RAM
 kvm2.tkk.internal - Ubuntu 24.04.2 LTS (GNU/Linux 6.8.0-142-generic x86_64) - 8GB RAM

<img width="1100" height="850" alt="ansible-libvirt-lab" src="https://github.com/user-attachments/assets/839f9c0a-1af2-431e-a678-6510bba6b687" />

SSH key access configured to both KVM hosts from the desktop (xor)

## Progressive guide
Follow each deep-dive guide to see the playbooks, logic, and terminal outputs:

1. **[Stage 1: Listing VMs](docs/01_listing_vms.md)** - Querying the hypervisors.
2. **[Stage 2: Storage Pool Management](docs/02_creating_pools.md)** - Setting up directory-based target pools.
3. **[Stage 3: Network Provisioning](docs/03_network_setup.md)** - Isolating internal lab bridges.
4. **[Stage 4: VM Deployment](docs/04_vm_provisioning.md)** - Templating XML domains and spawning guests.


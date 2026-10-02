# Using Ansible to manage KVM hosts
Here is the infrastructure:
A desktop (xor) with ansible
Two KVM hosts with libvirt/kvm installed already:
1. kvm1.tkk.internal - Ubuntu 24.04.2 LTS (GNU/Linux 6.8.0-136-generic x86_64) - 8GB RAM
2. kvm2.tkk.internal - Ubuntu 24.04.2 LTS (GNU/Linux 6.8.0-142-generic x86_64) - 8GB RAM

<img width="1100" height="850" alt="ansible-libvirt-lab" src="https://github.com/user-attachments/assets/839f9c0a-1af2-431e-a678-6510bba6b687" />

I have already set up key-based ssh login from xor to the hosts.

First I tested connectivity with the community.libvirt.virt module


```bash
tonny@xor:~/Documents/projects/ansible/libvirtsetup$ ansible-playbook -i ./hosts playbook.yaml

PLAY [configure kvm hosts] *******************************************************************************************************

TASK [Gathering Facts] ***********************************************************************************************************
ok: [kvm2.tkk.internal]
ok: [kvm1.tkk.internal]

TASK [List vms] ******************************************************************************************************************
ok: [kvm1.tkk.internal]
ok: [kvm2.tkk.internal]

PLAY RECAP ***********************************************************************************************************************
kvm1.tkk.internal          : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
kvm2.tkk.internal          : ok=2    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

tonny@xor:~/Documents/projects/ansible/libvirtsetup$

```

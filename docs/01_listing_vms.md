# RTFM
I started by reading the documentation.

```bash
tonny@xor:~/Documents/projects/ansible/libvirtsetup$ ansible-doc community.libvirt.virt

```

# No terminal output at first

Just using list_vms command is not enough.
The output is not sent to the terminal.
You can view the playbook state for this step here [v0.01.01_listing_vms_no_terminal_output](https://github.com/tonnykamuti/ansible-libvirt-kvm/releases/tag/v0.01.01_listing_vms_no_terminal_output)

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

There is really no output at first unless we capture output from list_vms in a variable using register and then output it using debug
# Raw json output

Adding the register variable and sending the json output to the terminal.
See this here [v0.01.02_listing_vms_raw_json_terminal_output](https://github.com/tonnykamuti/ansible-libvirt-kvm/releases/tag/v0.01.02_listing_vms_raw_json_terminal_output) 

<details>

```bash
tonny@xor:~/Documents/projects/ansible/libvirtsetup$ ansible-playbook -i hosts  playbook.yaml

PLAY [configure kvm hosts] *******************************************************************************************************

TASK [Gathering Facts] ***********************************************************************************************************
ok: [kvm2.tkk.internal]
ok: [kvm1.tkk.internal]

TASK [List vms] ******************************************************************************************************************
ok: [kvm2.tkk.internal]
ok: [kvm1.tkk.internal]

TASK [Print Vms] *****************************************************************************************************************
ok: [kvm1.tkk.internal] => {
    "msg": {
        "changed": false,
        "failed": false,
        "list_vms": [
            "kvm1obsd77_3",
            "misery",
            "kvm1ubusvr2",
            "carrie",
            "kvm1almalinux1",
            "kvm1ubusvr_template",
            "kvm1fbsd_clone_1",
            "toystory",
            "tfcikvm1fbsduefiunsecurezfs_0",
            "wormhole",
            "kvm1nbsd0",
            "kvm1fbsd0",
            "opensuseleap156_clone_1",
            "kvm1obsd77_2",
            "kvm1debsvr1",
            "kvm1almalinux_clone_2",
            "kvm1debsvr2",
            "kvm1almalinux_clone_1",
            "ci_kvm1ubusvr0",
            "tfkvm1alpine0",
            "solaris11",
            "tf_ci_kvm1_ubusvr1",
            "tf_kvm1_uefi_debsvr_0",
            "shining",
            "tfcikvm1fbsd_0",
            "kvm1ubusvr1",
            "kvm1almalinux_clone_0",
            "kvm1ubusvr3",
            "kvm1obsd77_0",
            "kvm1fbsd_template",
            "opensuseleap156",
            "opensuseleap156_cloned_template",
            "kvm1obsd77_1",
            "kvm1debsvr_template",
            "monsters-inc",
            "shrek",
            "kvm1almalinux_template",
            "kvm1fbsd_clone_0",
            "tfcikvm1fbsd_1"
        ]
    }
}
ok: [kvm2.tkk.internal] => {
    "msg": {
        "changed": false,
        "failed": false,
        "list_vms": [
            "kvm2debsvr0",
            "kvm2debsvr3",
            "kvm2rhel9svr0",
            "server2",
            "server1",
            "kvm2alpine0",
            "kvm2rhel9svr1",
            "kvm2debsvr1",
            "kvm2debsvr2"
        ]
    }
}

PLAY RECAP ***********************************************************************************************************************
kvm1.tkk.internal          : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
kvm2.tkk.internal          : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

tonny@xor:~/Documents/projects/ansible/libvirtsetup$

```

</details>


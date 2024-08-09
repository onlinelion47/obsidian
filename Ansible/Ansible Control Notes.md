Created a VM called `ansible-control-01`
Created two other nodes:
`almalinux8-00`
`almalinux8-01`

Created sysadmin `gurudarbar` with admin privileges on each VM


On the control node install ansible:
```bash
sudo dnf install ansible-core -y
```

#### Create an inventory:
```bash
[gurudarbar@ansible-control-01 ~]$ cat /etc/ansible/hosts
# This is the default ansible 'hosts' file.
#
# It should live in /etc/ansible/hosts
#
#   - Comments begin with the '#' character
#   - Blank lines are ignored
#   - Groups of hosts are delimited by [header] elements
#   - You can enter hostnames or ip addresses
#   - A hostname/ip can be a member of multiple groups

# Ex 1: Ungrouped hosts, specify before any group headers:

## green.example.com
## blue.example.com
192.168.122.42
192.168.122.195
```
#### Setup ssh
From sysadmin (non-root account):
```bash
ssh-keygen
ssh-copy-id gurudarbar@almalinux8-00.local
ssh-copy-id gurudarbar@almalinux8-01.local
```


#### Test it out:
```bash
ansible -m ping all
```

#### Returns:
```bash
[gurudarbar@ansible-control-01 ~]$ ansible all -m ping
192.168.122.195 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": false,
    "ping": "pong"
}
192.168.122.42 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/libexec/platform-python"
    },
    "changed": false,
    "ping": "pong"
}
```

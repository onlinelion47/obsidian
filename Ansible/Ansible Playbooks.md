
#### Notes:
Ansible is written in YAML
 Playbooks seem to be mostly written as lists of dictionaries:
 eg:
 ```yaml
 # A list of tasty fruits:
- Apple
- Banana
- Mango
- Pineapple
- Date

# A dictionary of an employee record
301707:
  name: Mark Davis
  job: System Administrator
  skill: Elite

# A YAML playbook:
---
- name: Update web servers
  hosts: 'alma*'
  remote_user: gurudarbar

  tasks:
  - name: Ensure apache is at the latest version
    ansible.builtin.yum:
      name: httpd
      state: latest

  - name: Write the apache config file
    ansible.builtin.template:
      src: /srv/httpd.j2
      dest: /etc/httpd.conf

- name: Update db servers
  hosts: 'alma*'
  remote_user: gurudarbar

  tasks:
  - name: Ensure postgresql is at the latest version
    ansible.builtin.yum:
      name: postgresql
      state: latest

  - name: Ensure that postgresql is started
    ansible.builtin.service:
      name: postgresql
      state: started

```


#### Idea:
- Setup NFS server with ansible
- setup clients with access
- Have some base/common things for all the VMS
    - vim
    - bash-completion
    - STIG?



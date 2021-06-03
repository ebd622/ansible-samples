# Basic

* Inventory and playbooks
* [Modules](#mudules)
* [Variables](#variables)
* [Conditions](#conditions)
* [Loops](#loops)


## Inventory and playbooks

Run module `ping` in command line
```
ansible target1 -m ping -i inventory.txt
ansible target2 -m ping -i inventory.txt --user=osboxes
ansible all -m ping -i inventory.txt --user=osboxes
```
Run a playbook:
```
ansible-playbook playbook-ping.yaml -i inventory.txt
ansible-playbook playbook-ping.yaml -i inventory.txt --user=osboxes
```

[Copy](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/copy_module.html) a file to targets:
```
ansible-playbook playbook-copy.yaml -i inventory.txt
ansible-playbook playbook-copy.yaml -i inventory.txt --user=osboxes
```

## Modules
Ansible modules are combined in different groups depending on provided functionalities.
These are some moules:
* System
* Commands
* Files
* Database
* Cloud
* ...
  
More modules are here: https://docs.ansible.com/ansible/2.8/modules/list_of_all_modules.html

## Variables

1. Run a playbook with default vars:
```
ansible-playbook playbook-vars.yaml -i inventory.txt --user=osboxes
```

2. Run a playbook with `extra-vars` and ovewrride default var-values:
```
ansible-playbook playbook-vars.yaml -i inventory.txt --user=osboxes --extra-vars "line1='Override line1' line2='Override line2'"
ansible-playbook playbook-vars.yaml -i inventory.txt --user=osboxes --extra-vars '{\"line1\"=\"Override line1\",\"line2\"=\"Override line2\"}'
```

## Conditions
TODO

### Create a file
Create a file `test-cond.txt` in targets with a Linux Distribution's name
```
ansible-playbook cond-playbook.yaml -i inventory.txt --user=osboxes
```

### Install and run Nginx
Sudo password can be provided via a special ansible variable `ansible_sudo_pass`:
```
ansible-playbook nginx-playbook.yaml -i inventory.txt --user=osboxes --extra-vars "ansible_sudo_pass=osboxes.org
```

Stop Nginx:
```
ansible-playbook nginx-playbook.yaml -i inventory.txt --user=osboxes --extra-vars "ansible_sudo_pass=osboxes.org state=stopped"
```

## Loops
Here are some examples on how to create loops

### Create a file with users
Create a file with user names:
```
ansible-playbook loop1-playbook.yaml -i inventory.txt --user=osboxes
```
Create a file with user name-s and uid-s:
```
ansible-playbook loop2-playbook.yaml -i inventory.txt --user=osboxes
```

### Install packages
Install packages listed in var with `loop`:
```
ansible-playbook packages-playbool.yaml -i inventory.txt --user=osboxes --extra-vars "ansible_sudo_pass=osboxes.org"
```

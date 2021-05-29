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


```
ansible-playbook playbook-vars.yaml -i inventory.txt --user=osboxes --extra-vars "line1='Override line1' line2='Override line2'"
ansible-playbook playbook-vars.yaml -i inventory.txt --user=osboxes --extra-vars '{\"line1\"=\"Override line1\",\"line2\"=\"Override line2\"}'
```


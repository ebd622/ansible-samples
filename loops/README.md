## Loops
TODO

### Create a file with users
File with user names will be created on targets
```
ansible-playbook loop-playbook.yaml -i inventory.txt --user=osboxes
```

### Install packages
Packages listed in var-s will be installed with `loop`:
```
ansible-playbook packages-playbool.yaml -i inventory.txt --user=osboxes --extra-vars "ansible_sudo_pass=osboxes.org"
```
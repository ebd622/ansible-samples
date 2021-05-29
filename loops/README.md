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
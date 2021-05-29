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
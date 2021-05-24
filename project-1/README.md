# Inventory and playbooks

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




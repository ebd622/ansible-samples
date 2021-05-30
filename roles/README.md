## Roles
A primary purpose of roles is to make your work reusable.
Key points about roles:
* Roles help to organise your work in Ansible;
* Roles help to share your work within Ansible community;

### Create your own role
To create your own role `myrole` run the command:
```
ansible-galaxy init myrole
```
This will create a directory structure:
```
myrole
|
 - defaults/
 - files/
 - handlers/
 - meta/
 - README.md
 - tasks/
 - templates/
 - tests/
 - vars/
```

### Search for existing role
To search for `mysql` role run the command:
```
ansible-galaxy search mysql
```
This will give you list of available roles, for example:
```
 Name                                                  Description
 ----                                                  -----------
 acandid.mysql                                         Install MySQL 8 on RedHat/CentOS 8 and Create user and database.
 achaussier.mysql-backup                               configure mysql-backup with xtrabackup and mysqldump
 achaussier.mysql-server                               Install mysql-server package
 adarnimrod.mysql                                      Provision a MySQL server
 adelean.solr                                          Apache Solr for Linux.
 AdopteUnOps.mysql-docker                              Ansible role to run a mysql container.
 AdopteUnOps.rancher-install-master                    Install rancher master
 ...
```

### Use role

#### 1. Check where a role would be installed
First you can check where roles whould be installed:
```
$ ansible-config dump | grep ROLE

DEFAULT_PRIVATE_ROLE_VARS(default) = False
DEFAULT_ROLES_PATH(default) = [u'/home/ebd/.ansible/roles', u'/usr/share/ansible/roles', u'/etc/ansible/roles']
GALAXY_ROLE_SKELETON(default) = None
GALAXY_ROLE_SKELETON_IGNORE(default) = ['^.git$', '^.*/.git_keep$']
```

#### 2. Install a role

```
ansible-galaxy install adarnimrod.mysql
```
This will install a role in your home:

```
$ ansible-galaxy install adarnimrod.mysql

- downloading role 'mysql', owned by adarnimrod
- downloading role from https://github.com/adarnimrod/mysql/archive/master.tar.gz
- extracting adarnimrod.mysql to /home/ebd/.ansible/roles/adarnimrod.mysql
- adarnimrod.mysql (master) was installed successfully
```


You can also install a role in a custom location (for example, in the current directory under /role):
```
ansible-galaxy install adarnimrod.mysql -p ./roles
```

#### 3. List currently installed roles:
```
ansible-galaxy list
```

#### 4. Use a role in your playbook
Specify a role as an array of strings:
```
- name: Install and confihure MySQL
  hosts: db-server
  roles:
    - adarnimrod.mysql
```

Specify a role as an array of dictionaries:
```
- name: Install and confihure MySQL
  hosts: db-server
  roles:
    - adarnimrod.mysql
      become: yes
      vars:
        mysql_user_name: db-user
```

### Examples
#### Install and run mysql server
(Here are some details about the role: https://github.com/geerlingguy/ansible-role-mysql)

##### 1. Install a role
```
ansible-galaxy install acandid.mysql
```
##### 2. Deploy and start MySQL on a target:
```
ansible-playbook mysql-playbook.yaml -i inventory.txt --user=osboxes --extra-vars "ansible_sudo_pass=osboxes.org
```

#### Install and run Docker
(Here are some details about the role: https://github.com/acandid/docker)

##### 1. Install a role
```
ansible-galaxy install acandid.docker
```
##### 2. Deploy and start Docker on a target:
```
ansible-playbook docker-playbook.yaml -i inventory.txt --user=osboxes --extra-vars "ansible_sudo_pass=osboxes.org
```
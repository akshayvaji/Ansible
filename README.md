# Ansible

Ansible role to install and configure Mysql 5.7, Java(sunjdk), Resin(Port 8080), Tomcat(Port 8081)

> How to use this role

# Clone the Project:
```
$ git clone https://github.com/akshayvaji/Ansible.git
```
```
$ cd ansible
```
Update your inventory, e.g:
```
$ vi inventory.ini
```
```
[ama]
x.x.x.x       # Remote user to act on
```
```
$ vi serversetup.yml
```
```
- name: Serversetup deployment playbook
  hosts: ama       # Inventory hosts group / server to act on
  become: yes               # If to escalate privilege
  become_method: sudo       # Set become method
  remote_user: root         # Update username for remote server
  vars:
    tomcat_ver: 9.0.30                          # Tomcat version to install
    ui_manager_user: manager                    # User who can access the UI manager section only
    ui_manager_pass: Str0ngManagerP@ssw3rd      # UI manager user password
    ui_admin_username: admin                    # User who can access bpth manager and admin UI sections
    ui_admin_pass: Str0ngAdminP@ssw3rd          # UI admin password
  roles:
    - mysql57
    - java
    - tomcat
    - resin
```    
If you are using non root remote user, then set username and enable sudo:
```
become: yes
become_method: sudo
```
> PS: Need to download rpm package of sunjdk from https://www.oracle.com/java/technologies/javase-jdk8-downloads.html and put it under /roles/java/files -- rpm size (171MB) - Unable to upload due to size limit

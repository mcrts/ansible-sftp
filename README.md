# ansible-sftp

SFTP server configuation with Ansible (using Vagrant).\
With a sftp jail at /jail.\
Disable ssh connection for users under the sftpg group.

----

### Requirements
* Ansible v2.9 (not tested with previous release)
* Vagrant (the working example is using vagrant to provision environment)

### How to use
```console
user@host:~$ vagrant up
user@host:~$ vagrant ssh mgmt
```

```console
vagrant@mgmt:~$ ssh-keyscan sftpserver >> .ssh/known_hosts
vagrant@mgmt:~$ ssh-keygen -t rsa -b 2048
vagrant@mgmt:~$ ansible-playbook playbooks/ssh_addkey.yml --ask-pass
vagrant@mgmt:~$ ansible-playbook playbooks/sftp_install.yml
vagrant@mgmt:~$ ansible-playbook playbooks/adduser.yml
What is your username?: martin
What is your password?:
confirm What is your password?:
```

```console
vagrant@mgmt:~$ sftp martin@sftpserver
ftpuser@sftpserver's password: 
Connected to sftpserver.
sftp>
```

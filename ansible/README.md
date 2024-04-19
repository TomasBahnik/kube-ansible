# kube-ansible

Manage k8s by Ansible

## Ansible host system

Managed nodes need python

* `docker pull python`
* run container in interactive mode `docker run -it python /bin/bash` so it stays running
* verify `python --version`
* list running containers `docker ps`
* find container IP address `docker inspect <ID or name> | grep IPAddress` (either container ID or name)
* add local authorized keys for `root` 
  * `docker cp ./authorized_keys <ID or name>:/root/.ssh/authorized_keys`
* check / install `ssh` service : `service ssh status` / `apt-get install -y openssh-server`
* edit `/etc/ssh/sshd_config` : PermitRootLogin without-password, PasswordAuthentication no (`apt-get install vim` to install vim)
* save changes `docker commit <ID or name> python_ssh_root`

```shell
ssh root@172.17.0.2
Linux b12ac565ef02 6.5.0-27-generic #28~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Mar 15 10:51:06 UTC 2 x86_64
```

* ansible myhosts -m ping -i inventory.ini -u root

```shell
(kube-ansible) toba@inspiron-15-7000:~/git/github/kube-ansible/ansible_quickstart$ ansible myhosts -m ping -i inventory.ini -u root
172.17.0.2 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
```

```shell
ansible-playbook -i inventory.ini playbook.yaml -u root
```
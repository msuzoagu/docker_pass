Role Name
=========
Sets up docker to use pass for authentication via docker_credential_helpers


Requirements
------------
- Docker 
  If following security best practice and running docker as non-root user, note that due to [tty](https://lists.gnupg.org/pipermail/gnupg-users/2016-October/056854.html) [owership](https://dev.gnupg.org/T2739) [requirements](https://dev.gnupg.org/T3908), this role is effective only when: 
  + docker
  + [docker_credential_helpers](https://github.com/docker/docker-credential-helpers)
  have both been installed and configured BEFORE this role is run as role does not make use of sudo commands.  

Role tested on: 
  - docker-ce | 5:18.09.1~3-0~ubuntu-xenial 


### Operating System
  - Ubuntu:
    - Bionic 18.04 (LTS) (x64)


Role Variables
--------------
See examples in _vars_ folder


Dependencies
------------
None


Example Playbook
----------------
Given `playbook_path/file_name`: 

    - name: Use docker-credential-pass for authentication 
        hosts: docker_hosts
        gather_facts: yes
        remote_user: "{{ docker_user.name }}" 
        vars: 
            ansible_ssh_private_key_file: "{{ docker_user.private_key }}"
        roles:  
            - docker_pass

run: 

  `ansible-playbook -i inventory_path playbook_path/file_name.yaml`


License
-------
BSD


Author Information
------------------
msuzoagu

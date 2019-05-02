Role Name
=========

Sets up docker to use pass for authentication via docker_credential_helpers

Requirements
------------

### Docker 
If following security best practice and running docker as non-root user, note that due to [tty](https://lists.gnupg.org/pipermail/gnupg-users/2016-October/056854.html) [owership](https://dev.gnupg.org/T2739) [requirements](https://dev.gnupg.org/T3908), this role is effective only when: 
- docker
- [docker_credential_helpers](https://github.com/docker/docker-credential-helpers)
have both been installed and configured BEFORE this role is run as role does not make use of sudo commands.  

Tested on the following docker versions: 
- docker-ce | 5:18.09.1~3-0~ubuntu-xenial 

### Operating System
Ubuntu:
- Bionic 18.04 (LTS) (x64)

Role Variables
--------------

See examples in *vars* folder

Dependencies
------------
A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - name: Use docker-credential-pass for authentication 
        hosts: swarm_cluster
        gather_facts: yes
        remote_user: "{{ docker_user.name }}" 
        vars: 
            ansible_ssh_private_key_file: "{{ docker_user.private_key }}"
        roles:  
            - docker_credential_pass

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).

Role Name
=========

mongodb: Mongodb

[![Build Status](https://travis-ci.org/cmihai-ansible/mongodb.svg?branch=master)](https://travis-ci.org/cmihai-ansible/mongodb)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.mongodb](https://galaxy.ansible.com/devops-toolbox.mongodb)

```bash
ansible-galaxy install devops-toolbox.mongodb
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
mongodb_packages_state: present
mongodb_remove_packages: true
mongodb_enable_service: true
mongodb_enable_selinux: true
mongodb_copy_templates: true
mongodb_firewall_configure: true
mongodb_firewall_rules:
  - service: ssh
  - port: 3389
mongodb_users:
  - user: devops
    group: docker
mongodb_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install mongodb on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: mongodb is configured
      import_role:
        name: devops-toolbox.mongodb
      vars:
        mongodb_packages_state: present
        mongodb_remove_packages: true
        mongodb_enable_service: true
        mongodb_enable_selinux: true
        mongodb_copy_templates: true
        mongodb_firewall_configure: true
        mongodb_firewall_rules:
          - service: ssh
          - port: 3389
        mongodb_users:
          - user: devops
            group: docker
        mongodb_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: mongodb
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)

Role Name
=========

A developing role for deploying consul cluster to AWS.

Requirements
------------

Uses EC2 modules. Requires boto and AWS credentials.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
---
- hosts: localhost
  become: false
  gather_facts: false
  connection: local
  vars:
    consul_encrypt_key: '{{ vault_consul_encrypt_key }}'
    consul_ssh_key: jdelaporte-vault-ansible
    consul_terminate: False
    consul_instance_type: t2.small
    consul_data: '/opt/consul'
    consul_user: 'consul'
    consul_group: '{{ consul_user }}'
    consul_home: '/etc/consul.d'
    consul_version: '1.7.1'
    consul_download_url: 'https://releases.hashicorp.com/consul/{{ consul_version }}/consul_{{ consul_version }}_linux_amd64.zip'
    consul_install_dir: '/usr/local/bin'
    consul_ami_owner: "amazon"
    consul_ami_name_filter: "amzn2-ami-hvm-2.0.????????.?-x86_64-gp2"
    consul_cluster_name: primary
    consul_cluster_region: us-east-2
    consul_cluster_ami_id: ami-0e38b48473ea57778 #DONE: make this discoverable
    consul_cluster_count: 3
    consul_cluster_tags:
      deployment: green
      lifecycle: dev
      product: vault

  roles:
  - consul_cluster_aws
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).

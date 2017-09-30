Role Name: nfcapd
=================

This role sets up the nfcapd damon using nfdump package on Ubuntu or Debian.

Requirements
------------

This role was tested on the following platforms.

### Ansible
- Version 2.4

### Distributions
- Ubuntu 16.04
- Debian 9

Role Variables
--------------

### Defaults
    nfcapd_logdir: '/var/cache/nfdump'
    * The directory stores all collected data by nfcapd.

    nfcapd_logdir_perms:
      - { owner: 'root', group: 'root', mode: '0755' }
    * The 'nfcapd_logdir' permissions
  
    nfcapd_port: '2055'
    * The listener port of nfcapd

    nfcapd_subdir_type: '1'
    * The number specify the subdir type passed to the argument of '-S' option of nfcapd.

    nfcapd_daemon_uidgid:
      - { user: 'root', group: 'root' }
    * The nfcapd daemon running with specified user and group permissions

Dependencies
------------

N/A

Example Playbook
----------------

    - hosts: all
      vars:
  	    - nfcapd_logdir_perms:
          - { owner: 'root', group: 'root', mode: '0750' }
        - nfcapd_port: '2055'
        - nfcapd_subdir_type: '1'
      roles:
        - yasuhiroabe.nfcapd

License
-------

Apache License 2.0

Author Information
------------------

[Yasuhiro ABE](http://www.yasundial.org/foaf.xml)


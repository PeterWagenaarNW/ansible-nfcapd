Role Name: nfcapd
=================

This role sets up the nfcapd daemon using nfdump package on Ubuntu or Debian.

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
    * The 'nfcapd_logdir' and sub-directories permission will be overwritten according to this setting.
  
    nfcapd_port: '2055'
    * The listener port of nfcapd

    nfcapd_subdir_type: '1'
    * The number will be passed to the argument of nfcapd '-S' option.

    nfcapd_daemon_uidgid:
      - { user: 'root', group: 'root' }
    * The nfcapd daemon running with specified user and group permissions.
	  The permission of the directory which places the pid file will be overwritten according to this setting.

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


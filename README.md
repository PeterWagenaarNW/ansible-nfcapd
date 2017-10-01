Role Name: nfcapd
=================

This role sets up the nfcapd daemon using nfdump package on Ubuntu or Debian.

Requirements
------------

This role is tested on the following platforms.

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
    * The nfcapd daemon running with the specified user and group permissions.
	  The permission of the directory which places the pid file will be overwritten according to this setting.
	  If you use this option, please also consider the 'nfcapd_logdir_perms' setting if the nfcapd process is able to write the flow data to that path.

    nfcapd_listen_address: '127.0.0.1'
	* The nfcapd daemon running with the specified network address.
	
Dependencies
------------

1. This role forces to restart the nfcapd and fprobe process because nfcapd will be lost the packet from fprobe if restarted.

2. This role uses the *killall* command to stop the process. 

Example Playbook
----------------

    - hosts: all
      vars:
  	    - nfcapd_logdir_perms:
          - { owner: 'root', group: 'root', mode: '0750' }
        - nfcapd_port: '2055'
        - nfcapd_subdir_type: '1'
      roles:
        - YasuhiroABE.nfcapd

License
-------

Apache License 2.0

Author Information
------------------

[Yasuhiro ABE](http://www.yasundial.org/foaf.xml)


Ansible Role: client ntp
=========

This role set up NTP client for a GNU/Linux server.

Requirements
------------

None.

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # Name of the ntp service and ntp package (depends on your OS, can be ntp, ntpd...)
    ntp_service_name: ntpd
    ntp_package: ntp

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      roles:
        - client_ntp

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.

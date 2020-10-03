Ansible Role: icinga2_server
=========

This role deploys Icinga2, MariaDB and Icingaweb2 on a GNU/Linux server.

Requirements
------------

None.

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml`

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: icinga2_server
      roles:
        - icinga2_server

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.

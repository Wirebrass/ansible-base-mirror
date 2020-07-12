Ansible Role: mnin-async
=========

This role set up munin-async service for a GNU/Linux server.

Requirements
------------

Munin node installed on nodes.

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # Name of the munin-async service and munin-async package (depends on your OS, can be munin-async, munin-asyncd...)
    munin-async_service_name: munin-asyncd
    munin-async_package: munin-async
    
    # SSH pubkey of Munin server
    munin_async_authorized_keys: []
    
    # Munin async user
    munin_async_user: munin-async

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      roles:
        - munin-async

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.

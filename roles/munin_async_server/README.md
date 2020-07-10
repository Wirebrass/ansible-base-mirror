Ansible Role: munin async server
=========

This role set up Munin async server for a GNU/Linux server.

Requirements
------------

The role geerlingguy.munin needs to be deploy on the Munin server before using the current role.

Roll Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # Name of the munin-async service and munin-async package (depends on your OS, can be munin-async, munin-asyncd...)
    munin_async_service_name: munin-async
    munin_async_package: munin-async
    
    # Private/Public SSH keys of Munin async server to access all Munin async client account
    private_key_munin_async_user_host: ""
    public_key_munin_async_user_host: ""

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: munin_server
      roles:
        - munin_async_server

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.

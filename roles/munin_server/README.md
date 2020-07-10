Ansible Role: munin server
=========

This role set up Munin server for a GNU/Linux server.

Requirements
------------

The role geerlingguy.munin needs to be deploy on the Munin server before using the current role.

Roll Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # Private/Public SSH keys of Munin server to access all Munin async client account
    private_key_munin_user_host: ""
    public_key_munin_user_host: ""
    
    # Munin user and group
    munin_user: "munin"
    munin_group: "munin"
    
    # Munin user home directory
    munin_home_directory: "/var/lib/munin"


Dependencies
------------

None.

Example Playbook
----------------

    - hosts: munin_server
      roles:
        - munin_server

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.

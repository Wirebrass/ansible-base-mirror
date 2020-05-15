Ansible Role: users sudo
=========

This role defines users in sudo group on a GNU/Linux server.

Requirements
------------

None.

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # HASH of Default user password when a new user is created
    default_user_password: ""
    
    # Liste of all sudo users
    sudo_users: []
    
    # SSH public key of users to allow SSH connection witk SSH priv/pub keys
    public_key: []

**WARNING :** all of these variables must be defined, else you may have some errors (use vault).

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      roles:
        - users_sudo

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.

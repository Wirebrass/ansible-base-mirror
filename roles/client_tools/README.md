Ansible Role: client tools
=========

This role install packages (tools) on a GNU/Linux server.

Requirements
------------

None.

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # All packages (tools) to install on the server
    tools_package:
      - sudo
      - curl
      - sed
      - grep
      - net-tools

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      roles:
        - client_tools

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.

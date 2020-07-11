Ansible Role: client resolvers
=========

This role defines DNS resolvers to use for a GNU/Linux server.

Requirements
------------

None.

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # DNS resolvers to use
    resolvers:
      - 2001:910:800::40
      - 80.67.169.12
      - 2001:913::8
      - 80.67.188.188
    
    # Domain to use in the DNS "search" resolver field
    main_domain: wirebrass.fr 
    
    # Set to true if you want to configure resolvers with Ansible
    configure_resolvers: true

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      roles:
        - client_resolvers

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.

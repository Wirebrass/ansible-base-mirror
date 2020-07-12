Ansible Role: systctl customization
=========

This role set up sysctl customization for a GNU/Linux server.

Requirements
------------

None.

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # Sysctl swapiness value
    sysctl_vm_swapiness: 10
    
    # Sysctl config file
    sysctl_config_file: /etc/sysctl.d/56-ansible.conf

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      roles:
        - sysctl_customizations

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.

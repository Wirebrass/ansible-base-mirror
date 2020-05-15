Ansible Role: client iptables
=========

This role defines iptables rules for a GNU/Linux server.

Requirements
------------

None.

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # All authorized TCP ports
    tcp_authorized_ports:
      - 22
    
    # All incoming authorized IP
    ip_authorized: []

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      roles:
        - client_iptables

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.

Ansible Role: client iptables
=========

This role defines iptables rules for a GNU/Linux server (but NOT for routers).

Requirements
------------

WARNING : do not apply this role on routers !!!

This role assumes you have a clean iptables configuration on your host (else, you may need to flush the current rules).

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # All authorized TCP ports
    tcp_authorized_ports:
      - 22
    
    # All authorized UDP ports
    udp_authorized_ports: []
    
    # All incoming authorized IP
    ip_authorized: []
    
    # Set to false to avoid iptables configure with this role
    configure_iptables: true

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

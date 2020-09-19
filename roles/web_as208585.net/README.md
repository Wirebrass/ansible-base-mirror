Ansible Role: web_as208585.net
=========

This role deploys as208585 webfiles on a GNU/Linux server.

Requirements
------------

None.

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # Files location for as208585.net website
    website_location: "/var/www/html/as208585.net"

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: web_server
      roles:
        - web_as208585.net

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.

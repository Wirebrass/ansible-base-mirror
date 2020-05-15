Ansible Role: auto upgrade
=========

This role defines a contask to auto-upgrade a GNU/Linux server.

Requirements
------------

None.

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # Cron task scheduling for auto upgrade
    cron_upgrade_minute: "0"
    cron_upgrade_hour: "2"
    cron_upgrade_day: "*"
    cron_upgrade_month: "*"
    cron_upgrade_weekday: "*"
    
    # Set to true if you want to enable auto upgrade
    auto_upgrade: false
    
    # Name of the cron service and cron package (depends on your OS, can be cron, cronie, crond...)
    cron_service_name: cron
    cron_package: cron
    
    # Default upgrade task configured for Debian
    cron_upgrade_job: export PATH=$PATH:/usr/local/sbin:/usr/sbin:/sbin; export TERM=rxvt-unicode-256color; apt-get -q update && apt-get -q -y upgrade && apt-get -q -y autoremove

*WARNING :* by default, the `cron_upgrade_job` is configured for Debian family distribution, you need to change the value if you are using another OS.

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      roles:
        - auto_upgrade

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.

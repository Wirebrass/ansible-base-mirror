Ansible Role: auto reboot
=========

This role defines a contask to auto-reboot a GNU/Linux server.

Requirements
------------

None.

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # Cron task scheduling for auto reboot
    cron_reboot_minute: "0"
    cron_reboot_hour: "3"
    cron_reboot_day: "*"
    cron_reboot_month: "*"
    cron_reboot_weekday: "*"

    # Set to true if you want to enable auto reboot
    auto_reboot: false

    # Name of the cron service and cron package (depends on your OS, can be cron, cronie, crond...)
    cron_service_name: cron
    cron_package: cron

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      roles:
        - auto_reboot

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.

Ansible Role: backup_client
=========

This role set up a GNU/Linux backup client.

Requirements
------------

You need a valid postfix configuration on your host (to send email reports).

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # Name of the cron service and cron package (depends on your OS, can be cron, cronie, crond...)
    cron_client_service_name: cron
    cron_client_package: cron
    
    # Name of the Borkbackup package
    borgbackup_package: borgbackup
    
    # Backup client folders to backup (separated with a space)
    backup_client_folders_to_backup: ""
    
    # Folder to deploy backup client scripts
    backup_scripts_folder: "/usr/local/sbin"
    
    # Backup client user and home directory
    backup_client_user: "root"
    backup_client_user_home: "/root"
    
    # Crontask backup client scheduling
    backup_client_cron_weekday: "*"
    backup_client_cron_hour: "1"
    backup_client_cron_minute: "30"
    
    # Alias config file
    aliases_config_file: "/etc/aliases"
    
    # User or email to send client backup scripts report
    backup_client_mail_target: "root"
    
    # Compression parameters
    backup_client_compression_param: "lzma,9"

**NOTE :** this role will only configure backup client on host if `backup_client_folders_to_backup` is not empty.

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: all
      roles:
        - backup_client

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.


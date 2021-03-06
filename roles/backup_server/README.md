Ansible Role: backup_server
=========

This role set up a GNU/Linux backup server.

Requirements
------------

You need private/public SSH keys to access GIT repositories to backup.

Role Variables
--------------

All variables and default values are defined in `defaults/main.yml` :

    # Private/public SSH keys for the backup user on the backup server to access GIT repositories to backup
    private_key_backup_user_host: ""
    public_key_backup_user_host: ""
    
    # GIT repositories to backup
    git_repositories: []
    
    # Name of the cron service and cron package (depends on your OS, can be cron, cronie, crond...)
    cron_client_service_name: cron
    cron_client_package: cron
    
    # Name of the GIT package
    git_package: git
    
    # Name of the Borkbackup package
    borgbackup_package: borgbackup
    
    # Backup folder
    backup_folder: "/data"
    
    # Folder to deploy backup scripts
    backup_scripts_folder: "/usr/local/sbin"
    
    # GIT backup user
    backup_user_git: "backup-git"
    
    # Crontask GIT backup scheduling
    backup_git_cron_weekday: "*"
    backup_git_cron_hour: "1"
    backup_git_cron_minute: "30"
    
    # Crontask GIT archive backup scheduling
    backup_git_archive_cron_weekday: "*"
    backup_git_archive_cron_hour: "2"
    backup_git_archive_cron_minute: "30"
    
    # Alias config file
    aliases_config_file: "/etc/aliases"
    
    # User or email to send GIT backup scripts report
    backup_git_mail_target: "root"

**WARNING :** you need to define all of these variables, else you may have errors (use ansible-vault).

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: backup_server
      roles:
        - backup_server

License
-------

BSD

Author Information
------------------

This role was created in 2020 by Nemo.


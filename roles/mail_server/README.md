# Ansible Role: Mail Server

Installs postfix on RedHat/CentOS, Gentoo or Debian/Ubuntu.

## Requirements

If you're using this as an SMTP relay server, you will need to do that on your own, and open TCP port 25 in your server firewall.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    postfix_config_file: /etc/postfix/main.cf
    aliases_config_file: /etc/aliases

The path to the Postfix `main.cf` and aliases configuration file.

    postfix_service_state: started
    postfix_service_enabled: yes

The state in which the Postfix service should be after this role runs, and whether to enable the service on startup.

    postfix_inet_interfaces: localhost
    postfix_inet_protocols: all

Options for values `inet_interfaces` and `inet_protocols` in the `main.cf` file.

    alias_email: "{{ system_admin_email }}"

The email address of admin user (to receive system notification).

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - postfix

## License

MIT / BSD


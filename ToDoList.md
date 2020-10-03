# ToDoList (not exhaustive)

* Complete iptables role for routers (FORWARD, NAT, ...).
* Complete sysctl customizations role for routers (forward) and RA.
* Create Icinga2 server (conf hosts) and clients roles.
* Add a pre-task which can install python-apt, gentoolkit or python-yum if not installed (with shell module).
* Add roles for different function:
  * **DNS authority**
  * **DNS resolvers**
  * **OpenVPN server**
  * **Wireguard server (or tinc ?)**
  * **BGP router**
  * **Key server**
  * **LDAP server**
  * **Mail server**
  * **DOH server**
  * **Weechat + IRC Relay**
  * GIT
  * Pad/Paste/...
  * Build server (Gentoo builds)
  * Nextcloud
  * Zabbix/LibreNMS/autres trucs à tester
  * Tests (ex: restauration backup)
  * Kubernetes cluster

## More...

* Role munin-async: add possibility to deploy multiple SSH keys (if multiple Munin server).
* Role munin-node: add some plugins / custom configurations for more details.
* Test deploy all the infrastructure to validate ansible-base.
* Role icinga2_server: add hosts.conf and hosts files via ansible (and not manually)

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
  * **LDAP server**
  * **DOH server**
  * **Weechat + IRC Relay**
  * Build server (Gentoo builds)

## More...

* Role munin-async: add possibility to deploy multiple SSH keys (if multiple Munin server).
* Role munin-node: add some plugins / custom configurations for more details.
* Role icinga2_server: add hosts.conf and hosts files via ansible (and not manually)

# MySQL Server (`mysql-server`)

**Part of the BAS Ansible Role Collection (BARC)**

Installs and secures MySQL database server with an optional app database

## Overview

* Installs MySQL package with python bindings required by ansible.
* Configures accounts for local users (root, controller and app) with full permissions for root/controller.
* Configures external access, if desired, and configures allowed hosts for mysql users as required
* Secures installation by removing test database and the anonymous user
* Optionally creates an app database assigning the app mysql user full access

## Author

[British Antarctic Survey](http://www.antarctica.ac.uk) - Web & Applications Team

Contact: [basweb@bas.ac.uk](mailto:basweb@bas.ac.uk).

## Availability

This role is designed for internal use but if useful can be shared publicly.

## License

[Open Government Licence V2](https://www.nationalarchives.gov.uk/doc/open-government-licence/version/2/)

## Requirements

### BAS Ansible Role Collection (BARC)

* `core`

## Variables

* `mysql_server_root_user_password`
    * Default password for root user.
    * Default: "precipice-08563%"
* `mysql_server_controller_user_password`
    * Default password for controller user.
    * Default: "cacophony-234/877"
* `mysql_server_app_user_password`
    * Default password for app user.
    * Default: "infamous-&34529"
* `mysql_server_bind_address`
    * The address/interface on which to listen for incoming connections.
    * By default this will bind to the servers external IP to allow external access, to prevent this set this value to "localhost"
    * Default: "{{ ansible_eth1.ipv4.address }}"
* `mysql_server_default_allowed_hosts_all_users`
	* Controls the list of hosts (local or remote) the root user can connect from.
	* **Do not override this variable**, use `mysql_server_default_allowed_hosts_<user>_user` to set extra default hosts for a user or `mysql_server_user_allowed_hosts_<user>_user` to set extra hosts for a user.
    * Structured as an array of addresses (IP/hostname/FQDN)
    * Default: [array]
        * "127.0.0.1"
        * "localhost"
* `mysql_server_allowed_hosts_app_user`
    * Controls the list of hosts (local or remote) the app user can connect from.
	* "127.0.0.1" and "localhost" values MUST be specified in this variable for Ansible to interact with the database.
	* "localhost" MUST be the last item in this variable, see [here](http://ansible.cc/docs/modules.html#mysql-user) for details.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: [array]
        * "127.0.0.1"
        * "localhost"
* `mysql_server_default_allowed_hosts_root_user`
	* Controls the list of hosts (local or remote) the root user can connect from.
	* **Do not override this variable**, use `mysql_server_user_allowed_hosts_root_user` instead.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: []  (empty array)
* `mysql_server_default_allowed_hosts_controller_user`
	* Controls the list of hosts (local or remote) the controller user can connect from.
	* **Do not override this variable**, use `mysql_server_user_allowed_hosts_controller_user` instead.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: []  (empty array)
* `mysql_server_default_allowed_hosts_app_user`
	* Controls the list of hosts (local or remote) the app user can connect from.
	* **Do not override this variable**, use `mysql_server_user_allowed_hosts_app_user` instead.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: []  (empty array)
* `mysql_server_user_allowed_hosts_root_user`
	* Controls the list of hosts (local or remote) the root user can connect from.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: []  (empty array)
* `mysql_server_user_allowed_hosts_controller_user`
	* Controls the list of hosts (local or remote) the controller user can connect from.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: []  (empty array)
* `mysql_server_user_allowed_hosts_app_user`
	* Controls the list of hosts (local or remote) the app user can connect from.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: []  (empty array)
* `mysql_server_create_app_db`
    * If "true" a database named "app" will be created with the app user assigned full access.
    * Default: "false"

## Changelog

### 0.2.0 - October 2014

* Refactoring allowed hosts variables into default and user variables (per MySQL user) for consistency with other roles
* Adding mysql controller user with root permissions
* Adding option to create an app database
* Fixing misspelt variables
* Refactoring allowed hosts variables
* New mysql controller user is used to create mysql app user

### 0.1.4 - October 2014

* Fixing invalid version number
* Fixing non-updated allowed_hosts variables for root and app user accounts preventing login

### 0.1.3.1 - October 2014

* Migrating role into BARC - this version should be a drop in replacement for any previous versions of this role
* Minor refactoring

### 0.1.3 - August 2014

* Fixing style used for expressing default bind-address (again), makes no overall changes

### 0.1.2 - August 2014

* Fixing style used for expressing default bind-address, makes no overall changes

### 0.1.1 - July 2014

* Fixing slight misconfiguration with default bind-address, makes no overall changes

### 0.1.0 - June 2014

* Initial version

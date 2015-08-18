# MySQL Server (`mysql-server`)

**Part of the BAS Ansible Role Collection (BARC)**

Installs and secures MySQL database server with an optional app database

## Overview

* Installs MySQL package with python bindings required by ansible.
* Configures accounts for local users (root, controller and app) with full permissions for root/controller.
* Configures external access, if desired, and configures allowed hosts for mysql users as required
* Secures installation by removing test database and the anonymous user
* Optionally creates an app database assigning the app mysql user full access

## Availability

This role is designed for internal use but if useful can be shared publicly.

## Usage

### Requirements

#### BAS Ansible Role Collection (BARC)

* `core`

### Variables

* `mysql_server_root_mysql_user_password`
    * Default password for MySQL root user.
    * Default: "password"
* `mysql_server_controller_mysql_user_enabled` 
	* If "true" a user for database server management tasks, termed a controller user, will be created with root privileges.
	* Default: true
* `mysql_server_controller_mysql_user_username`
	* The username of the controller MySQL user, used for managing the database server, if enabled
	* This variable **must** be a valid MySQL user
	* Default: "controller"
* `mysql_server_controller_mysql_user_password`
    * Default password for MySQL controller user.
    * Default: "password"
* `mysql_server_app_mysql_user_enabled` 
	* If "true" a user for day to day database tasks, termed an app user, will be created with no initial privileges.
	* Default: true
* `mysql_server_app_mysql_user_username` 
	* The username of the app MySQL user, used for day to day database tasks, if enabled
	* This variable **must** be a valid MySQL user
	* Default: "app"
* `mysql_server_app_mysql_user_password`
    * Default password for MySQL app user.
    * Default: "infamous-&34529"
* `mysql_server_default_allowed_hosts_all_mysql_users`
	* Controls the default list of hosts (local or remote) all MySQL users can connect from.
	* **Do not override this variable**
		* Use `mysql_server_user_allowed_hosts_all_mysql_users` to set extra hosts for all users.
		* Use `mysql_server_default_allowed_hosts_<user>_mysql_user` to set per user default hosts.
		* Use `mysql_server_user_allowed_hosts_<user>_mysql_user` to set extra hosts for a user.
    * Structured as an array of addresses (IP/hostname/FQDN)
    * Default: [array]
        * "127.0.0.1"
        * "localhost"
* `mysql_server_default_allowed_hosts_root_mysql_user`
	* Controls the default list of hosts (local or remote) the root MySQL user can connect from.
	* **Do not override this variable**, use `mysql_server_user_allowed_hosts_root_mysql_user` instead.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: []  (empty array)
* `mysql_server_default_allowed_hosts_controller_mysql_user`
	* Controls the default list of hosts (local or remote) the controller MySQL user can connect from.
	* **Do not override this variable**, use `mysql_server_user_allowed_hosts_controller_mysql_user` instead.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: []  (empty array)
* `mysql_server_default_allowed_hosts_app_mysql_user`
	* Controls the default list of hosts (local or remote) the app MySQL user can connect from.
	* **Do not override this variable**, use `mysql_server_user_allowed_hosts_app_mysql_user` instead.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: []  (empty array)
* `mysql_server_user_allowed_hosts_all_mysql_users`
	* Controls the list of hosts (local or remote) all MySQL users can connect from.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: []  (empty array)
* `mysql_server_user_allowed_hosts_root_mysql_user`
	* Controls the list of hosts (local or remote) the root MySQL user can connect from.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: []  (empty array)
* `mysql_server_user_allowed_hosts_controller_mysql_user`
	* Controls the list of hosts (local or remote) the controller MySQL user can connect from.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: []  (empty array)
* `mysql_server_user_allowed_hosts_app_mysql_user`
	* Controls the list of hosts (local or remote) the app MySQL user can connect from.
	* Structured as an array of addresses (IP/hostname/FQDN)
	* Default: []  (empty array)
* `mysql_server_create_app_db`
    * If "true" a database named "app" will be created with the app user assigned full access.
    * Default: "false"
* `mysql_server_bind_address`
    * The address/interface on which to listen for incoming connections.
    * By default this will bind to the servers external IP to allow external access, to prevent this set this value to "localhost"
    * Default: "{{ ansible_eth1.ipv4.address }}"

## Contributing

This project welcomes contributions, see `CONTRIBUTING` for our general policy.

## Developing

### Committing changes

The [Git flow](https://github.com/fzaninotto/Faker#formatters) workflow is used to manage development of this package.

Discrete changes should be made within *feature* branches, created from and merged back into *develop* (where small one-line changes may be made directly).

When ready to release a set of features/changes create a *release* branch from *develop*, update documentation as required and merge into *master* with a tagged, [semantic version](http://semver.org/) (e.g. `v1.2.3`).

After releases the *master* branch should be merged with *develop* to restart the process. High impact bugs can be addressed in *hotfix* branches, created from and merged into *master* directly (and then into *develop*).

### Issue tracking

Issues, bugs, improvements, questions, suggestions and other tasks related to this package are managed through the BAS Web & Applications Team Jira project ([BASWEB](https://jira.ceh.ac.uk/browse/BASWEB)).

## License

Copyright 2015 NERC BAS. Licensed under the MIT license, see `LICENSE` for details.

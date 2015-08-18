# MySQL Server (`mysql-server`) - Changelog

* Updating default password variables for consistency to highlight they should be changed
* Updating dates for licenses
## 0.3.4 - December 2014

* Preparing role for public release

## 0.3.3 - October 2014

* Fixing more instances of incorrect login user when creating app user (was using app instead of controller)
* Fixing incorrect login user when creating app database (was using app instead of controller)

## 0.3.2 - October 2014

* Fixing incorrect login user when creating app user (was using app instead of controller)

## 0.3.1 - October 2014

* Fixing broken variable

## 0.3.0 - October 2014

* Updating dependencies
* Refactoring variables, all existing variables have been renamed to avoid confusion between OS users and MySQL users
* Usernames for controller and app users, both OS and MySQL, are now configurable using variables
* Controller and app MySQL users are now optional, though enabled by default
* Preparing for public release

## 0.2.0 - October 2014

* Refactoring allowed hosts variables into default and user variables (per MySQL user) for consistency with other roles
* Adding mysql controller user with root permissions
* Adding option to create an app database
* Fixing misspelt variables
* Refactoring allowed hosts variables
* New mysql controller user is used to create mysql app user

## 0.1.4 - October 2014

* Fixing invalid version number
* Fixing non-updated allowed_hosts variables for root and app user accounts preventing login

## 0.1.3.1 - October 2014

* Migrating role into BARC - this version should be a drop in replacement for any previous versions of this role
* Minor refactoring

## 0.1.3 - August 2014

* Fixing style used for expressing default bind-address (again), makes no overall changes

## 0.1.2 - August 2014

* Fixing style used for expressing default bind-address, makes no overall changes

## 0.1.1 - July 2014

* Fixing slight misconfiguration with default bind-address, makes no overall changes

## 0.1.0 - June 2014

* Initial version

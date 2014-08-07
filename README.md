vagrant-typo3cms
================

Vagrant setup for TYPO3CMS. Ansible will install all required setups for the server environment.
TYPO3 environment checks will just run fine.

Environment
--------------
* OS: Ubuntu 12.04 LTS (precise) x86_64

* Database: MySQL 5.5.x
::
    username / password: typo3 / typo3

This user is also allowed to connect from outside the virtual machine.

* PHP: PHP 5.4.x (with Xdebug v2.2.3)

Installation
--------------

*used VirtualBox 4.3.14, Vagrant 1.6.3 & Ansible 1.6.10*

1. Install both: Vagrant & Ansible

https://www.vagrantup.com/downloads.html

http://docs.ansible.com/intro_installation.html

2. Install plugin vagrant-vbguest to sync VirtualBox Guest Additions
::
    vagrant plugin install vagrant-vbguest

3. Modify your host database (e.g. /etc/hosts)
::
    192.168.13.37   dev.typo3.local

4. Run command "vagrant up" to start

It will take some time depending on your bandwith

5. Setup TYPO3

Extract TYPO3 source/dummy package to folder src/ and navigate to http://dev.typo3.local in your browser.

6. Follow installation instructions

7. Run command "vagrant halt" to shutdown

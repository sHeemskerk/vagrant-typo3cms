Vagrant setup for TYPO3CMS
================

Ansible will install all required packages for the server environment.
TYPO3 environment checks will just run fine.

Environment
--------------
* __OS__: Ubuntu 12.04 LTS (precise) x86_64

* __Database__: MySQL 5.5.x

   Following user will be setup on provision:
   ```
   username/password: typo3/typo3
   ```
   This user is also allowed to connect from outside the virtual machine.

* __PHP__: PHP 5.4.x (with Xdebug v2.2.3)

Installation
--------------
*used VirtualBox 4.3.14, Vagrant 1.6.3 & Ansible 1.6.10*

1. Install both: [Vagrant](https://www.vagrantup.com/downloads.html) & [Ansible](http://docs.ansible.com/intro_installation.html)

2. Install plugin vagrant-vbguest to sync VirtualBox Guest Additions

    ```
    vagrant plugin install vagrant-vbguest
    ```

3. Modify your host database (e.g. /etc/hosts)

    ```
    192.168.13.37   dev.typo3.local
    ``` 

4. Run command `vagrant up` to start

    It will take some time depending on your bandwith

5. Setup TYPO3

    Extract TYPO3 source/dummy package to folder src/ and navigate to http://dev.typo3.local in your browser.

6. Follow installation instructions

7. Run command `vagrant halt` to shutdown

ToDos
--------------
* include PHP suhosin extension

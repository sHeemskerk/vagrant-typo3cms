Vagrant setup for TYPO3CMS
================

Ansible will install all required packages for the server environment.
TYPO3 environment checks will just run fine.

*NOTE:* As there is no Ansible client for Windows at the time, this setup will only work on
Linux/Unix machines.

Environment
--------------
* __OS__: Ubuntu 12.04 LTS (precise) x86_64

* __Database__: MySQL 5.5.x

   Following user will be setup on provision:
   ```
   username/password: typo3/typo3
   ```
   This user is also allowed to connect from outside the virtual machine.

* __PHP__: PHP 5.5.x (with Xdebug v2.2.5)

* __MailCatcher__: 0.6.1 (check out http://192.168.13.37:1080)

Installation
--------------
*used VirtualBox 4.3.20, Vagrant 1.7.2 & Ansible 1.8.2*

1. Install both: [Vagrant](https://www.vagrantup.com/downloads.html) & [Ansible](http://docs.ansible.com/intro_installation.html)

2. Install plugin vagrant-vbguest to sync VirtualBox Guest Additions

    ```
    vagrant plugin install vagrant-vbguest
    ```

3. Run command `vagrant up` to start

    It will take some time depending on your bandwith

4. Modify your host database (e.g. /etc/hosts)

    ```
    sudo sh -c 'echo "192.168.13.37 t3-cms.dev" >> /etc/hosts'
    ``` 

5. Create folder `mkdir -p vHosts/t3-cms/Web` and extract TYPO3 source/dummy package:

    ```
    wget "http://get.typo3.org/6.2.9" -O typo3_src.tgz 
    tar xvzf typo3_src.tgz 
    mv typo3_src-6.2.9 typo3_src 
    ln -s typo3_src/typo3 typo3 
    ln -s typo3_src/index.php index.php 
    touch FIRST_INSTALL
    ```

6. Setup TYPO3

     Navigate to http://t3-cms.dev in your browser and follow installation instructions

7. Run command `vagrant halt` to shutdown

ToDos
--------------
* include PHP suhosin extension

Credits
--------------
1. http://subugoe.github.io/devsettings/vagrant.html
2. https://gist.github.com/robertlemke/4951820


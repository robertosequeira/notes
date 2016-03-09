# Ubuntu

* Shutdown/Restart server

  ```
  $ sudo reboot
  $ sudo poweroff
  ```

* Update ubuntu from the command line

  https://help.ubuntu.com/community/AptGet/Howto

  ```
  $ sudo apt-get update && sudo apt-get dist-upgrade
  ```



# Server setup

* If there are problems with locale configuration

  ```
  $ locale
  $ sudo locale-gen es_CR.UTF-8
  $ sudo nano /etc/default/locale
  
    LANG="es_CR.UTF-8"
    LANGUAGE="es_CR.UTF-8"
    LC_ALL="es_CR.UTF-8
  ```

* Add a new user

  `$ adduser deploy`

* Add new user to sudo group

  `$ gpasswd -a deploy sudo`

## SSH access

* Generate new ssh key for new user

  `$ ssh-keygen`

* Add key to remote server for new user

  ```
  $ ssh-copy-id -i ~/.ssh/new-key_rsa.pub deploy@server-ip
  ```

* Edit ssh config to disable root login

  `$ sudo nano /etc/ssh/sshd_config`

* Set PermitRootLogin to no

  `PermitRootLogin no`

* Restart ssh service

  `$ sudo service ssh restart`

#Firewall

* Add required firewall rules

  ```
  $ sudo ufw allow ssh  
  $ sudo ufw allow 80/tcp
  # SSL/TLS
  $ sudo ufw allow 443/tc
  # SMTP
  $ sudo ufw allow 25/tcp
  ...
  ```

* Verify added rules

  `$ sudo ufw show added`

* Enable/disable firewall

  ```
  $ sudo ufw enable
  $ sudo ufw disable
  ```

## Configure timezone

  `$ sudo dpkg-reconfigure tzdata`

## NTP

* This will allow your computer to stay in sync with other servers (Time)

  ```
  $ sudo apt-get update
  $ sudo apt-get install ntp
  ```

## Swap

https://help.ubuntu.com/community/SwapFaq

* Create swap file

  ```
  $ sudo fallocate -l 1G /swapfile
  or
  $ sudo fallocate -l 512m /swapfile
  ```

* Finish swap configuration

  ```
  $ sudo chmod 600 /swapfile
  $ sudo mkswap /swapfile
  $ sudo swapon /swapfile
  $ sudo sh -c 'echo "/swapfile none swap sw 0 0" >> /etc/fstab'
  ```

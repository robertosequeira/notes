# Ubuntu

* Shutdown/Restart server

  ```
  $ sudo reboot
  $ sudo poweroff
  ```

* Update ubuntu from the command line

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

## Nginx

* Install nginx

  ```
  $ sudo apt-get update
  $ sudo apt-get install curl git-core nginx -y
  ```

# Postgress

* Install
  ```
  $ sudo apt-get update
  $ sudo apt-get install postgresql postgresql-contrib
  ```

* Verify access

  ```
  $ sudo -i -u postgres
  $ psql
  $ \q
  $ exit
  ```

* Create role and set password

  ```
  $ sudo -i -u postgres
  $ createuser --interactive
  # Create rails role
  $ psql
  $ \password rails
  $ \q
  $ exit
  ```

* Delete a existing role

  ```
  $ sudo -i -u postgres  
  $ psql
  $ DROP ROLE role_name;
  $ \q
  $ exit
  ```


* List existing databases

  ```
  $ sudo -i -u postgres
  $ psql
  $ \list
  $ \q
  $ exit
  ```

* List existing roles

  ```
  $ sudo -i -u postgres
  $ psql
  $ \du
  $ \q
  $ exit
  ```

* Create a new DB

  ```
  $ sudo -i -u postgres
  $ createdb hello`
  $ exit
  ```


* Get info about current connection (User, database, etc.)

  `conninfo`

* Connect to postgres specifying connection information

  ```
  psql -U postgres -d rails -h 127.0.0.1 -W
  psql -U postgres -h 127.0.0.1
  ```

  | Paramenter  | Description |
  | :---------: | ----------- |
  | -U          | User        |
  | -d          | Database    |
  | -h          | Host        |


# RVM - Ruby

* Add RVM, ruby and create a custom gemset

  ```
  $ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
  $ curl -sSL https://get.rvm.io | bash -s stable
  $ source ~/.rvm/scripts/rvm
  $ rvm requirements
  $ rvm install 2.2.1
  $ rvm use 2.2.1 --default
  $ rvm use 2.2.1@my_gemset --create
  ```

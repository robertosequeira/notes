# Rails Server Configuration

## Ubuntu configuration

### 1. Non root account

```shell
$ adduser academy

# add new user to sudo group
$ usermode -aG sudo academy

# verify user was created
$ cut -d: -f1 /etc/passwd
```

### 2. SSH access

```shell
# generate a new key
$ ssh-keygen

# Add a SSH alias (~\.ssh\config)
#Host academy
#  HostName      192.168.0.104
#  User          academy
#  IdentityFile  ~/.ssh/academy_rsa

# add the new key to the server
$ ssh-copy-id -i .ssh/academy_rsa academy
```
```shell
# disable root login and password login
$ sudo nano /etc/ssh/sshd_config

# Update file to:
# PermitRootLogin [no|prohibit-password]
# PasswordAuthentication no

# restart ssh service
$ sudo service ssh restart
```

### 3. Firewall

```shell
# list already registered apps
$ sudo ufw app list

# register a new exception
$ sudo ufw allow OpenSSH

# show added exceptions
$ sudo ufw show added

# enable the firewall
$ sudo ufw enable

# verify firewall status
$ sudo ufw status
```

### Time zone and NTP

```shell
$ sudo apt-get update
$ sudo apt-get install ntp
```

## PostgreSQL Configuration

### 1. Installation

```shell
$ sudo apt-get install postgresql postgresql-contrib libpq-dev
```

### 2. Login role

```shell
# impersonate postgres user
$ sudo -i -u postgres
$ sudo su - postgres

# access postgres interactive terminal
$ psql

# list existing roles
$ \du

# list existing databases
$ \list

# exit from postgres terminal
$ \q

# create a new role
$ createuser --interactive
$ createuser academy
$ createuser -s academy

# set role password
$ psql
$ \password academy
$ \q

# create role database
$ createdb academy
```
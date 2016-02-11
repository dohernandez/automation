# Automation
This repository contains the ansible automation code to build a simple PHP environment

## Before starting
### VM settings
To edit additional configuration options exposes in VirtualBox-powered Vagrant environments,  
copy the `config/box_setting.dist.yml` to `config/box_setting.yml` and the edit it.

```
# Box settings

# The name that appears in the VirtualBox GUI
name: dohernandez.dev
# The memory ram
memory: 2048
# The cpus
cpus: 2
# The private network
ip: 10.10.10.200
# aliases to provide for your /etc/hosts.
alias: ["dev.dohernandez.io"]
```

### Ansible settings
To edit where Ansible can find its commands to run during the vagrant provision, 
copy the `config/box_setting.dist.yml` to `config/box_setting.yml` and the edit it.

```
# Ansible settings

limit: all
playbook: "ansible/playbook.yml"
# The roles defined:
#     - { role: server,    tags: ["server", "nginx", "mysql", "mongodb", "redis", "php", "xdebug", "composer", "app", "dev-app"] }
#     - { role: nginx,     tags: ["nginx", "app", "dev-app"] }
#     - { role: mysql,     tags: ["mysql", "app", "dev-app"] }
#     - { role: mongodb,   tags: ["mongodb", "dev-app"] }
#     - { role: redis,     tags: ["redis"] }
#     - { role: php,       tags: ["php", "app", "dev-app"] }
#     - { role: xdebug,    tags: ["xdebug", "dev-app"] }
#     - { role: composer,  tags: ["composer", "app", "dev-app"] }
#     - { role: app,       tags: ["app", "dev-app"] }
tags: server
```

### Ansible variable settings
To edit the Variables in Ansible used in all the roles available, 
copy the `ansible/var/all.dist.yml` to `ansible/var/all.yml` and the edit the file ...

```
---
server:
    ...
    packages: [vim, git, htop, nodejs, npm]
    timezone: UTC
    locale: pt_BR.UTF-8
nginx:
    ...
    docroot: /dohernandez/httpdocs # This server doc root have to correspond with the docroot variable defined in the box_setting file
    servername: dev.dohernandez.io # This server name have to correspond with one aliases defined to provide for your /etc/hosts.
mysql:
    ...
    root_password: dohernandez
    database: dohernandez
    user: dohernandez
    password: dohernandez
    dump: ''
redis:
    ...
    port: '6379'
php:
    ...
    ppa: php5-5.6
    packages: [php5-cli, php5-intl, php5-mcrypt, php5-curl, php5-mysql, php5-mongo]
```

## Software

Make sure you have the following software installed in your machine. If running OSX, just follow the instructions below.

+ [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
+ [Vagrant >=1.8.1](https://www.vagrantup.com/downloads.html)
+ [Git](https://git-scm.com/downloads)

### OSX Must-haves

[Homebrew](http://brew.sh/) and [Cask](http://caskroom.io/) make it very easy to install software on OSX.

```bash
# Install Homebrew
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

# Install Cask
brew install caskroom/cask/brew-cask

# Install git
brew install git

# Install virtualbox
brew cask install virtualbox

# Install vagrant and plugins
brew cask install vagrant
vagrant plugin install vagrant-hostmanager
```

## Booting up your local environment

To get started developing:

1. Clone this repository somewhere.
2. Cd into the repository
3. Run `vagrant up` to get the VM running.
4. Your application code go into Code can be add in `src/<app name>`, ex: `src/web`.

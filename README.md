# Automation
This repository contains the ansible automation code to build a simple PHP environment

## Before starting
### VM settings
VirtualBox provider exposes some additional configuration options that allow you 
to more finely control your VirtualBox-powered Vagrant environments. 
You can modify some of them here. Copy the `config/box_setting.dist.yml` to `config/box_setting.yml` and the edit the file, 
you will find something like ...

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
alias: ["dev.framework.io"]
```

### Ansible settings
Also we can tell to Ansible where to find the commands to run during the vagrant provision. 
Copy the `config/box_setting.dist.yml` to `config/box_setting.yml` and the edit the file ...

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

## Software

Make sure you have the following software installed in your machine. If running OSX, just follow the instructions below.

+ [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
+ [Vagrant >=1.8.1](https://www.vagrantup.com/downloads.html)
+ [Git](https://git-scm.com/downloads)

### OSX Must-haves

[Homebrew](http://brew.sh/) and [Cask](http://caskroom.io/) make it very easy to install software on OSX. This guide was written assuming their use.

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
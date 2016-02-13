# Automation
This repository contains the ansible automation code to build a simple PHP environment

## Before starting
### VM settings
To edit additional configuration options exposes in VirtualBox-powered Vagrant environments,  
copy the `config/box_setting.dist.yml` to `config/box_setting.yml` and edit the file.

### Ansible settings
To edit where Ansible can find its commands to run during the vagrant provision, 
copy the `config/box_setting.dist.yml` to `config/box_setting.yml` and edit the file.

### Ansible variable settings
To edit the Variables in Ansible used in all the roles available, 
copy the `ansible/var/all.dist.yml` to `ansible/var/all.yml` and the edit the file.

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
4. Your application code go into `src/<app name>`, ex: `src/laravel`.
5. Your public files go into `public/<files>`, ex: `public/index.php`.

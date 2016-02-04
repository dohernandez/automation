# Automation
This repository contains the ansible automation code to build a simple PHP environment

## Instances General Guidelines
1. All Instances should be created in the **private network** Subnet.

## Vagrant
The current vm is using the host port **1274** as an **ssh forwarded_port** and the ip **10.10.10.110**, in case you want to change those configurations because the port or the ip is being used,
or simple you don't' like it, you should edit the lines shown below into the Vagrantfile.

```
config.vm.network "forwarded_port", guest: 22, host: 1274, id: "ssh", auto_correct: true
...
config.vm.network :private_network, ip: "10.10.10.110"
```

## Requirements
1. Currently this was tested only on Macs, but should work with any nix. If you have Python 2.6 or 2.7 you're good to go.

## Instructions
Under some circumstances, El Capitain and VirtualBox have been known to cause problems. The vagrant box provided has been demonstrated to work with the following configurations:

1.  OSX 10.11.1<br />
    VirtualBox 5.0.8<br />
    Vagrant 1.7.4<br />
    Ansible 1.9.3<br />
<br />
2.  OSX 10.11.1<br />
    VirtualBox 4.3<br />
    Vagrant 1.7.2<br />
    Ansible 1.9.3<br />
<br />
3.  OSX 10.10.5<br />
    VirtualBox 5.0.2<br />
    Vagrant 1.7.4<br />
    Ansible 1.9.3<br />

### Environments
Each environment is represented by a file on the inventories level, usually `local.ini`, ect.

Each environment describes groups and instances that should live inside it plus some other environment variables. Take a moment to look at the local.ini environment file.

```
[dohernandez-web]
10.10.10.110
```

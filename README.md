# Automation
This repository contains the ansible automation code to build a simple PHP environment

# Before starting
## VM settings
VirtualBox provider exposes some additional configuration options that allow you 
to more finely control your VirtualBox-powered Vagrant environments. 
You can modify some of them here still. First copy the `config/box_setting.dist.yml` to `config/box_setting.yml` and the edit them

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

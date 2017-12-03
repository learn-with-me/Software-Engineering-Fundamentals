# Vagrant

Command line utility for managing the lifecycle of virtual machines in a single workflow. Vagrant is built on top of utilities like VirtualBox, and uses them internally. Advantage is to perform multiple tasks using a simple configuration file. This saves developers a lot of time in setting up the workspace and provide more time to focus on development.

> A tool focused on providing a consistent development environment workflow across multiple operation systems.

#### Features

```
Easy to use workflow
Focus on automation
Lower development environment setup time
Increases production parity
```

##### Provisioning

Vagrant doesn't do everything by itself, instead it works with 'Providers' and 'Provisioners' to help create these environments. Provisioners allow you to automatically install software, alter configurations, and more on the machine as part of vagrant up process. On the other hand, you can simply do `vagrant ssh` and install softwares yourself. Provisioning simply automates it.

Vagrant provisions machines on top of VirtualBox, VMware, AWS, etc. Then industry-standard provisioning tools such as shell scripts, Chef or Puppet can automatically install and configure software on the virtual machine.

You can configure nearly everything to be installed on the server. Most common provisioners used with Vagrant are `Puppet`, `Chef` and `Ansible` \(for staging and production environments\).

##### Terms

```
Box
A packaged Vagrant environment, typically a virtual machine

Provider
A provider provides virtualization support.
    Local: VirtualBox, VMware, Docker, Hyper-V
    Remote: AWS Cloud, Openstack

Vagrantfile
Configuration file for the target machine's config. Contains information like: Base image, hostname, network,
provisioner config (shell/automation tool)

Provisioner
A tool to setup virtual environment, can be as simple as a shell script or Chef, Puppet or Ansible
```

##### Steps to create a virtual machine

```
> mkdir myvagrantproject
> cd myvagrantproject
> vagrant init bento/centos-7.3
> vagrant up
```




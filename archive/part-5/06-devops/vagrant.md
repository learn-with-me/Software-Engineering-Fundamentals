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

##### Installation

```
# MacOS
$ brew cask install vagrant
```

##### Steps to create a virtual machine

```
Go to the desired folder
$ vagrant init bento/centos-7.3
$ vagrant init hashicorp/precise64
$ vagrant init ubuntu/trusty64 --minimal
$ vagrant up
# Note: By default Vagrant runs machines headless
```

##### Accessing/controlling the machine

```
$ vagrant ssh         # SSH into the box
> uname -a            # Unix Name command to print the unix kernel name

If you make a change to Vagrant configuration file, you can reload configuration by:
$ vagrant reload
$ vagrant provision    # Use this to provision the changes to the machine

Run from the folder that contains the Vagrantfile. This way Vagrant knows about the VM
$ vagrant suspend     # Suspends a machine
$ vagrant resume      # Revive the environment
$ vagrant halt        # Shuts down the VM. Doesn't take space in host system but takes time to resume
$ vagrant destroy -f  # Destry the VM completely. -f flag to skip asking confirmation
```

##### Vagrant Boxes

```
$ vagrant box -h          # Help on Vagrant commands
$ vagrant box list        # Lists all the boxes currently available locally
```

##### Synced Folders

Two standard ways to shared files between Guest and Host:

* Shared folders \(most popular\)
  * Files reside only on host
* rsync \(better approach\)
  * Syncs files by making a copy on change of file
  * Files are on both host as well as guest
  * Copy is only one way, from host to guest VM
  * Run `vagrant rsync-auto` for vagrant to watch for file changes in host machine

##### Look at

```
https://app.vagrantup.com/pricing
```




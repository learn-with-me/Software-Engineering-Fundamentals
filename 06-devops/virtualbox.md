# Oracle VirtualBox

##### links

```
Manual: https://www.virtualbox.org/manual/ch01.html
IE VMs: https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/
```

##### Guest OS

```
Ubuntu Linux Server
1. LTS
2. 64 bit

Download and install
https://www.ubuntu.com/download/server
```

##### Steps

```
1. Create a shared folder (for dev files and projects) - name it sandbox
2. Create the VM (from VirtualBox GUI). 1GB Ram should be fine for most cases.
3. Create Virtual hard drive (Persistent storage - for files and programs)
        Practically one single file stored on the host.
        No partitioning/formatting needed
        Create fixed size, since dynamic is one way only and slower
        Default size 10GB is plenty
4. Optimize the VM Configuration
        Processor - change from 1 to 2
        Extended features -> Enable PAE/NX
        Select image file
        Disable audio
5. Setting up custom port
        HTTP (default 80) - Allows webpages to be searched from Apache to a web browser.
                Apache runs on Guest at 80
                We're going to use 8080 for the host port
        MySQL DB (default 3306) - allows direct connections to the MySQL server for debugging, imports and so forth.
                Forward it to 9306 in the host
        MailCatcher (default 1080) - Utility that runs a simple receive only mail server and displays in web interface
                Used at times to reduce the risk of accidentally sending emails
                Forward it to 1080 on host as well. No changes.
        SSH (default 22) - Secure Shell. Forward it to port 2222 to avoid any conflicts

So far we have a Virtual Machine and no Server, this is where Ubuntu comes in. When setting it up, use the version of
Ubuntu that is optimized for virtualized environment.
Press F4 to view modes and select "Install a minimal virtual machine"

Set hostname in the installer's settings to identify the guest on our network
By default root is locked in Ubuntu, which means you can't login as root. You'll have to create a separate account that
has permissions to run programs as root

User Accounts in Linux
Full name - defaults, such as email
Username - use for logins

Setting up hostname
Every OS has a hosts file (a networking address book)
Mac - /etc/hosts                        Windows - %SystemRoot%/system32/drivers/etc/hosts
> sudo nano /etc/hosts

SSH (encrypted network protocol for secure data communication; even from unsecure servers)
SSH Service - runs on the server
SSH Client - connects to the service
SSH uses Public-Key cryptography (Two-linked keys)
        Public - Shared with target (encrypts and authenticates)
        Private - only on your computer (decrypts)
> ssh -p 2222 anshul@sandbox.dev
> ssh-keygen -t rsa -C "username@example.com"
> ssh -p2222 anshul@sandbox.dev mkdir -p .ssh
> cat ~/.ssh/id_rsa.pub
> cat ~/.ssh/id_rsa.pub | ssh -p2222 anshul@sandbox.dev 'cat >> .ssh/authorized_keys'
> nano ~/.ssh/config
        Host sandbox.dev
        Port 2222
        User anshul
```

##### VirtualBox additional dependencies

```
> sudo apt-get install build-essential        // tools for compiling
> sudo apt-get install virtualbox-dkms         // Dynamic Kernel Module support
> sudo apt-get install module-assistant        // handles kernel-module-source packages

Additional installations
> sudo apt-get install nano     - easy to use text editor
> sudo apt-get install zip      - utility for compressing archives
> sudo apt-get install unzip    - utility for decompressing archives
> sudo apt-get install curl     - download and debug HTTP
> sudo apt-get install man-db   - Display manuals
> sudo apt-get install acpid    - Advanced Configuration and Power Interface Daemon
                                  // To gracefully shutdown machine using VB power button
> sudo apt-get install git      - version control

After installation, you'll have to reboot the server
> sudo reboot


Share the path between the guest and the host
```

##### Notes

```
Virtual Box's default mode is Network Address Translation (NAT) where VB networking engine maps traffic from the VM.
In NAT mode, by default guest VM is unreachable from the network, including from your host on your computer and browser.
Instead, NAT uses Port forwarding, which is where NAT listens to networking traffic from one port and resends the
traffic to a different address and port. This configuration is bi-directional.
By default VB does not forward any ports. 
For security reasons, ensure you have a firewall enabled and blocking outside traffic.

We are going to forward traffic to four services necessary for managing a local development server. To avoid any
potential conflicts with services you may already be running, we're going to forward them to nonstandard ports. This is
not a replacement to security if you're not using a firewall. Security through obscurity is a delay tactic.

Note: Auto-capture keyboard will be ON by default when you start your virtual box.
To exit, press host key. On Mac, it is left-Command key. Windows -> right-Ctrl key
```




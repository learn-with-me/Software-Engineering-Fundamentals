# Debugging

How and what we need to setup debugging.

##### Terminal Commands

```
Network related
===============
$ ping 192.168.0.255    # Any IP ending with 255 is a broadcast IP (typically needed to refresh ARP list in next line)
                        # Remember 255 is due to the default subnet mask and can be changed by network admin
                        IP          192.168.1.151
                        Subnet Mask 255.255.255.0
                        The 0 is in the last field of the subnet mask, so you replace the last field of the IP address
                        with 255 and ping it: ping 192.168.1.255
$ arp -a                # View IPV4 & MAC Addresses of LAN Devices. Uses Address Resolution Protocol.
$ ndp -a                # View IPV6 instead
$ nslookup <hostname>   # Find IP for a specific device on the network. Try "nslookup localhost"
$ nslookup <webpage>    # Find IP for a specific webpage. Try "nslookup www.google.com"

Explore
    nmap - Network Discovery Tool
    fing

Note: Mobile apps can’t use the ARP table to view MAC addresses on iOS 11+ anymore. It also means apps will no longer
be able to assign custom names to discovered devices, because there is no longer a unique identifier for those network
cards. IP addresses can (and often do) change.
If this restriction affects your business, or even your home network, you can contact Apple as well and explain why
being able to reference MAC addresses is important to you. The company does listen to those customers.
```




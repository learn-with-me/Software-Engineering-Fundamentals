# Protocols

When it comes to application development, all of the communication is done on either TCP or UDP or even both protocols. Both of these protocols are at Transport layer level.

#### Basics of Protocols

##### TCP - Transport Control Protocol. Connection-oriented. Data delivery is guaranteed.

* FTP \[20/21\] \(File Transfer Protocol\) - 
* TFTP \[69\] \(Trivial File Transfer Protocol\) - Does not ask for user-id pwd
* SFTP \[22\] \(Secure File Transfer Protocol\) - Information is sent encrypted
* SSH \[22\] \(Secure Shell\) - To connect to another computer in a secured way
* Telnet \[23\] - To connect to another computer in unsecured way
* SMTP \[25/465\] \(Simple Mail Transfer Protocol\) - Mail protocol. Mail server to mail server.
  * Second port is used when using secured connection with encryption TLS/SSL
* IMAP4 \[143/993\] \(Internet Message Access Protocol\) - Mail protocol. Downloads a copy of message from the server
* POP3 \[110/995\] \(Post Office Protocol\) - Mail protocol. Downloads original message from the server, deleting from the server.
* HTTP \[80\] \(Hypertext Transfer Protocol\) - 
* HTTPS \[443\] \(Hypertext Transfer Protocol Secure\) - Uses SSL over HTTP

##### UDP - User Datagram Protocol. Connection-less. Data delivery is not guaranteed.

* SNMP \[161/162\] \(Simple Network Management Protocol\) - Used to sends infrastructure operation information
* NTP \[123\] \(Network Time Protocol\) - Server-sync is done over it
* SIP \[5060/5061\] \(Session Initiation Protocol\) - Video and Voice
* RTSP \[554\] \(Real Time Streaming Protocol\) - Stream media like YouTube or Hulu
* DHCP \[67/68\] \(Dynamic host Configuration Protocol\) - Provides an IP address to a computer/hardware

##### Both \(TCP and/or UDP\)

* LDAP \[389\] \(Lightweight Directory Access Protocol\) - 
* RDP \[3389\] \(Remote Desktop Protocol\) - Uses Windows. 
* DNS \[53\] \(Domain Name System\) - 

#### List of Protocols

* Ethernet Protocol - Link
  * IP - Internet
    * UDP - Transport
    * TCP - Transport
      * HTTP - Application
      * POP3 - Application

#### OSI Model \(Open Systems Interconnection\)

| Classification | Packet Data Unit | Layer | Description | Protocols |
| :--- | :--- | :--- | :--- | :--- |
| Host Layers | Data | Application Layer | Network process to application | HTTP, FTP, DNS, SNMP, Telnet, SMTP, IMAP, POP3, DCHP |
| Host Layers | Data | Presentation Layer | Data representation, Compression and Encryption | TLS, SSL, MPEG, ASCII chars, Compression |
| Host Layers | Data | Session Layer | Interhost Communication | NetBIOS, PPTP, SAP, RPC, SQL |
| Host Layers | Segments | Transport Layer | End-to-End connections and Reliability | TCP, UDP |
| Media Layers | Packets | Network Layer | Path Determination and IP \(Logical Addressing\) | IPV4, IPV6, ARP, ICMP \(ping\), IPSec, MPLS |
| Media Layers | Frames | Data Link Layer | MAC and LLC \(Physical Addressing\) | PPP, ATM, Ethernet, MPLS, 802.1x, FDDI, MAC address, Fiber Channel |
| Media Layers | Bits | Physical Layer | Media, Signal and Binary transmission | Ethernet, USB, Bluetooth, IEEE802.11, Cables, Connectors, Hubs |

TLS \(Transport Layer Security\)

SSL \(Secure Socket Layer\)

#### Communication Protocols

* P4
* LDAP
* Telnet
* HTTP
* RFC
* JDBC
* Session

#### API Protocols

* SOAP
* REST
* JSON-RPC
* gRPC
* GraphQL
* Thrift

#### IIoT Protocols

* MQTT
* AMQP
* REST
* OPC UA
* DHTP




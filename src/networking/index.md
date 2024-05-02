# Networking

## Transmission Control Protocol (TCP)

The protocol sits at layer 4 of the OSI model, and it is responsible for delivering the data segment between two nodes in a reliable and error-checked manner. The TCP consists of a 160-bit header that contains, among other fields, source and destination ports, a sequence number, an acknowledgment number, control flags, and a checksum.

TCP uses `datagram` sockets or ports to establish host-to-host communication, through designated ports such as port 80 for HTTP (web) and port 25 for SMTP (mail). The server listens on one of these well-known ports in order to receive communication requests from the client. The TCP connection is managed by the operating system with the socket representing the local endpoint for the connection.

The protocol operation consists of a `state machine`, which the machine needs to keep track of when it is listening for an incoming connection during the communication session, as well as releasing resources once the connection is closed. Each TCP connection goes through a series of states such as `Listen`, `SYN-SENT`, `SYN-RECEIVED`, `ESTABLISHED`, `FIN-WAIT`, `CLOSE-WAIT`, `CLOSING`, `LAST-ACK`, `TIME-WAIT`, and `CLOSED`. The different states help in managing the TCP messages.

TCP transmits data in an ordered and reliable fashion, thus guaranteeing delivery. It does this by first establishing a three-way handshake to synchronize the sequence number between the transmitter and the receiver, `SYN`, `SYN-ACK`, and `ACK`. The acknowledgment is used to keep track of subsequent segments in the conversation. Finally, at the end of the conversation, one side will send a `FIN` message, and the other side will `ACK`.

## User datagram protocol (UDP)

Unlike TCP, the header is only 64 bits, which only consists of a source and destination port, length, and checksum. The lightweight header makes it ideal for applications that prefer faster data delivery without setting up the session between two hosts or needing reliable data delivery. Perhaps it’s hard to imagine with today’s fast internet connections, but the lightweight header made a big difference to the speed of transmission in the early days of `X.21` and frame relay links. Also, not having to maintain various states, such as TCP, also saves computer resources.

Multimedia video streaming benefits from a lighter header when the application just wants to deliver the datagram as quickly as possible. The fast Domain Name System (DNS) lookup process is also based on the UDP protocol. The tradeoff between accuracy and latency usually tips to the side of low latency.

## Internet protocol



## Topics

* Local Area Network (LAN)
* Internet Service Provider (ISP)
* Internet of Things (IoT)
* Internet Protocol (IP)
* Dense Wavelength Division Multiplexing (DWDM)
* OSI Model
* Infrastructure as a Service (IaaS)
* Software-Defined Wide-Area-Networks (SD-WANs)
* International Organization for Standardization (ISO), now as Telecommunication Standardization Sector of the International Telecommunication Union (ITU-T)
* Advanced Research Projects Agency Network (ARPANET)
* Internet Assigned Numbers Authority (IANA)

## References

* [TCP Guide](http://www.tcpipguide.com/)
* [UDP Protocol](https://en.wikipedia.org/wiki/User_Datagram_Protocol)
* [Understanding sockets concepts](https://www.ibm.com/docs/en/zos/3.1.0?topic=concepts-understanding-sockets) | IBM
* [The difference between a Port and a Socket](https://www.baeldung.com/cs/port-vs-socket)

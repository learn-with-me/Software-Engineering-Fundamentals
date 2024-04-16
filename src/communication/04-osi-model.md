# OSI Model

Open Systems Interconnection (OSI) provides a common basis for system interconnection. In the OSI reference model, the communication between computing systems are split into seven different abstraction layers.

![Protocol Stack of the OSI Model](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/OSI_Model_v1.svg/400px-OSI_Model_v1.svg.png)

At each layer, two entities exchange data by means of a protocol.

## How Data Processing works?

Data processing by two communicating OSI-compatible devices proceeds as follows:

1. The data to be transmitted is composed at the topmost layer of the transmitting device (layer N) into a protocol data unit (PDU).
2. The PDU is passed to layer N-1, where it is known as the service data unit (SDU).
3. At layer N-1 the SDU is concatenated with a header, a footer, or both, producing a layer N-1 PDU. It is then passed to layer N-2.
4. The process continues until reaching the lowermost level, from which the data is transmitted to the receiving device.
5. At the receiving device the data is passed from the lowest to the highest layer as a series of SDUs while being successively stripped from each layer's header or footer until reaching the topmost layer, where the last of the data is consumed.

> Note: The lesser number of layers a protocol makes the data travel, it'll have reducing effect on the overall latency.

## Abstraction Layers (tabular)

| Classification | Packet Data Unit | Layer | Description | Protocols |
| :--- | :--- | :--- | :--- | :--- |
| Host Layers | Data | Application Layer (L7) | Network process to application | HTTP, FTP, DNS, SNMP, Telnet, SMTP, IMAP, POP3, DCHP |
| Host Layers | Data | Presentation Layer | Data representation, Compression and Encryption | TLS, SSL, MPEG, ASCII chars, Compression |
| Host Layers | Data | Session Layer | Interhost Communication | NetBIOS, PPTP, SAP, RPC, SQL |
| Host Layers | Segments | Transport Layer (L4) | End-to-End connections and Reliability | TCP, UDP |
| Media Layers | Packets | Network Layer | Path Determination and IP \(Logical Addressing\) | IPV4, IPV6, ARP, ICMP \(ping\), IPSec, MPLS |
| Media Layers | Frames | Data Link Layer | MAC and LLC \(Physical Addressing\) | PPP, ATM, Ethernet, MPLS, 802.1x, FDDI, MAC address, Fiber Channel |
| Media Layers | Bits | Physical Layer (L1) | Media, Signal and Binary transmission | Ethernet, USB, Bluetooth, IEEE802.11, Cables, Connectors, Hubs |

## Layer Architecture

| Layer | Protocol Data Unit | Function |
| :--- | :--- | :--- |
| L7 Application    | Data              | High-level protocols such as for resource sharing or remote file access, e.g. HTTP. |
| L6 Presentation   | Data              | Translation of data between a networking service and an application; including character encoding, data compression and encryption/decryption |
| L5 Session        | Data              | Managing communication sessions, i.e., continuous exchange of information in the form of multiple back-and-forth transmissions between two nodes |
| L4 Transport      | Segment, Datagram | Reliable transmission of data segments between points on a network, including segmentation, acknowledgement and multiplexing |
| L3 Network        | Packet            | Structuring and managing a multi-node network, including addressing, routing and traffic control |
| L2 Data Link      | Frame             | 	Transmission of data frames between two nodes connected by a physical layer |
| L1 Physical       | Bit, Symbol       | Transmission and reception of raw bit streams over a physical medium |

> Read more about each layer from the Wiki

## References

- Wiki - [OSI Model](https://en.wikipedia.org/wiki/OSI_model)

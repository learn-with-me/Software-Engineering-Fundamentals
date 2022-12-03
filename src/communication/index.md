# Communication

## How machines communicate?

Bytes are set of binary numbers, put together, they may mean something to someone, another thing to someone else. When bytes are put together, it may be referred as data. A machine is capable of transmitting/receiving data in form of bytes to/fron another machine. It's same like we know characters. Characters put together make words.

Transmitting data is one action. How would the data make sense to the one who is sending it or to the one receiving it?

The only way a word may make sense to us is by knowing two things:

1. Language that the word is written in
2. Word exists in our dictionary (for the language), which we refer to make sense out of what the word mean.

Similarly, for two entities/computers to communicate with each other and understand each other, they need a language to agree on. Think of it like a contract between systems, where one says "X", and it must mean something to another system. This language is what a `communication protocol` is. Fortunatley a computer's character set is defined and limited to 0's and 1's (binary data).

## Communication Protocol

A communication protocol is a formal descriptions of digital message formats and rules, that allows two or more entities to transmit information of any kind. The protocol defines the rules, syntax, semantics and synchronization of communication and possible error recovery methods, (a.k.a. language). Communication protocols have to be agreed upon by the parties involved. Communicating systems use well-defined formats for exchanging various messages.
Protocols may be implemented by hardware, software, or a combination of both.

## Protocol Stack

Multiple protocols can be used to describe different aspects of a single communication, known as a [protocol stack/suite](https://en.wikipedia.org/wiki/Protocol_stack).

Examples of Protocol stacks

| Protocol      | Layer                 |
| ------------- | -----------           |
| HTTP          | Application           |
| TCP           | Transport             |
| IP            | Internet or network   |
| Ethernet      | Link or data link     |
| IEEE 802.3ab  | Physical              |

![Protocol Stack of the OSI Model](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8d/OSI_Model_v1.svg/400px-OSI_Model_v1.svg.png)

## Designing a protocol

Let's say there is no protocol in the world that fits what I need. A protocol is just a contract that two systems agree to communicate on. Nothing stops me from building my own protocol.

While designing a protocol is easy, however desire to have it's widespread adoption is equally challenging. The only scenarios were someone would go this route are:

1. There is a real use case that requires a new protocol, that no one in the world has come across
2. You want your properitary hardware to communicate over unidentifiable communication method.

To complicate this further, none of the existing code/library will be able to read data based on the custom protocol, hence requiring a lot of code to be written from ground up.

## Standards Governance

[IETF](https://en.wikipedia.org/wiki/Internet_Engineering_Task_Force) - Internet Engineering Task Force is a standards organization for the internet and is responsible for the technical standards that make up the Internet protocol suite (TCP/IP) and publishes internet communication protocols.

[IEEE](https://en.wikipedia.org/wiki/IEEE) - Institute of Electrical and Electronics Engineers handles wired and wireless networking

[ISO](https://en.wikipedia.org/wiki/International_Organization_for_Standardization) - International Organization for Standardization handles other types

[ITU-T](https://en.wikipedia.org/wiki/ITU-T) - handles telecommunications protocols and formats for the [public switched telephone network](https://en.wikipedia.org/wiki/Public_switched_telephone_network) (PSTN)

### Organizations to know

- [IETF](https://en.wikipedia.org/wiki/Internet_Engineering_Task_Force) - Internet Engineering Task Force
- [IESG](https://en.wikipedia.org/wiki/Internet_Engineering_Steering_Group) - Internet Engineering Steering Group
- [IAB](https://en.wikipedia.org/wiki/Internet_Architecture_Board) - Internet Architecture Board
- [IRTF](https://en.wikipedia.org/wiki/Internet_Research_Task_Force) - Internet Research Task Force

## References

- Wiki - [Communication Protocol](https://en.wikipedia.org/wiki/Communication_protocol)
- Techopedia [Communication Protocol explained](https://www.techopedia.com/definition/25705/communication-protocol) blog
- [WebDAV Protocol](https://en.wikipedia.org/wiki/WebDAV)
- [Constrained Application Protocol](https://coap.technology) overview
  - Wiki - [Constrained Application Protocol](https://en.wikipedia.org/wiki/Constrained_Application_Protocol)
- Designing a protocol
  - National Cyber Security Centre - [Protocol Design Principles](https://www.ncsc.gov.uk/whitepaper/protocol-design-principles) whitepaper
  - [Designing your own protocol in 5 minutes](https://mayaposch.wordpress.com/2011/10/03/design-your-own-protocol-in-five-minutes/) blog
  - Quora [How to design protocol?](https://www.quora.com/How-do-I-design-and-write-my-own-network-protocol-like-TCP-IP-and-implement-it-in-C++)

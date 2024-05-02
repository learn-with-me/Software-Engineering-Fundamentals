# Internet

The Internet is a global computer network consisting of a web of inter-networks connecting large and small networks together.

`Hosts` are end nodes/devices on the network that communicate with other nodes. All nodes need to have an address, be routed, and be managed. These nodes request for services online, and the services are provided by `servers`.

The `network components` that connect nodes with servers fall in layer one to layer three of the 7-layer `OSI model`, sometimes even layer four. They are layer-two and layer-three routers and switches that direct traffic, as well as layer-one transports such as fiber optic cables, coaxial cables, twisted copper pairs, and some Dense Wavelength Division Multiplexing (DWDM) equipment, to name a few.

Collectively, hosts, servers, storage, and network components make up the internet.

## Internet Service Provider (ISP)

The ISP lets you get online. They do this by aggregating small networks into bigger networks that they maintain. Your ISP network often consists of many `edge nodes` that aggregate the traffic to their `core network`. The core network’s function is to interconnect these edge networks via a high-speed network.

At some of the more specialized edge nodes, called `Internet exchange points`, your ISP is connected to other ISPs to pass your traffic appropriately to your destination. The return path from your destination to your home device may or may not follow the same path through all these in-between networks back to your original device, while the source and destination remain the same. This asymmetrical behavior is designed to be `fault-tolerant` so that no one node can take down the whole connection.

## Data Centers

Because of the higher hardware capacity that servers demand, all required network components are often put together in a central location to be managed more efficiently. We often refer to these locations as data centers. They can generally be classified into three broad categories:

* Enterprise data centers
* Cloud data centers
* Edge data centers

Cloud data centers are so big and power-hungry that they are typically built close to power plants where they can get the cheapest power rate, without losing too much efficiency during the transportation of the power. Their cooling needs are so high that some are forced to be creative about where the data center is built. A typical network design would be a multi-staged Clos network.

The most significant limitation in routing the request and session all the way back from the client to a large data center is the latency introduced in the transport. Significant latency is where the network becomes a bottleneck. We can try to be as closely connected to the end-user as possible, perhaps meeting the user at the edge where the requests enter our network. We can place enough resources at these edge locations to serve the request.

This is especially common for servicing media content such as music and videos, by placing the media either inside or very near to the customer’s ISP. Also, for redundancy and connection speed, the upstreaming of the video server farm would not just be connected to one or two ISPs, but all the ISPs that we can connect to reduce the hop count, thus reducing the number of devices we need to pass thru. All the connections would have as much bandwidth as needed to decrease peak-hour latency. This need gave rise to the peering exchange’s edge data centers of big ISP and content providers.

Self-driving cars and Software-Defined Wide-Area-Networks (SD-WANs) are also applications of edge nodes. The self-driving car needs to make split-second decisions based on its sensors. SD-WAN routers need to route packets locally, without the need to consult a central “brain.” These are all concepts of intelligent edge nodes.

## The OSI Model

Networking breaks the complexity by using layers to model the functions of its elements. OSI is a conceptual model that componentizes the telecommunication functions into different layers. The model defines seven layers, and each layer sits independently on top of another one with defined structures and characteristics.

* Layer 1 (Physical)    - Sends data on to the physical wire
* Layer 2 (Data Link)   - Reads the MAC address from the data packet
* Layer 3 (Network)     - Reads the IP address from the packet
* Layer 4 (Transport)   - Responsible for the transport protocol (e.g., TCP, UDP) and error handling
* Layer 5 (Session)     - Establishes/ends connection between two hosts (e.g., NetBIOS, PPTP)
* Layer 6 (Presentation) - Formats the data so it can be viewed by the user (JPG, HTTPS, SSL, TLS). Also encrypts and decrypts.
* Layer 7 (Application) - Services that are used with end-user applications (like SMTP)

## References

* Book: [Mastering Python Networking](https://learning.oreilly.com/library/view/mastering-python-networking/9781803234618/)
* [TCP Guide](http://www.tcpipguide.com/)
* [UDP Protocol](https://en.wikipedia.org/wiki/User_Datagram_Protocol)
* OSI Model
    * [Image](https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781803234618/files/Images/B18403_01_03.png) | O'Reilly
    * [An OSI Model for Cloud](https://blogs.cisco.com/cloud/an-osi-model-for-cloud) | Cisco
    * [OSI Model Reference Guide](https://www.lifewire.com/osi-model-reference-guide-816289) | Livewire
    * [The OSI Model & It’s Importance to Cloud Engineers](https://medium.com/@gatambiasam/the-osi-model-its-importance-to-cloud-engineers-ebc10fab1deb) | Medium
    * [What is OSI Model?](https://aws.amazon.com/what-is/osi-model/) | AWS 

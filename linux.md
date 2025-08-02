# Linux Networking - Getting Started

## A Simple Network Model

We first define a simplified view of a computer network.

### Devices and Links

A network consists of *devices* connected via *links*. Devices are generally layer 2 (data link layer) devices such as switches, hubs and access points, or layer 3 (network layer) and above, such as end-user computers, routers and server computers. Devices are also called nodes. 

We generally will not deal much with layer 2 devices. They will be used, but not configured in Linux.

We divide layer 3 devices into two categories based on their ability to forward IP packets:

- *Hosts*: will not forward IP packets. End-user computers (PCs, laptops) are typically hosts, and computers running servers may also be a host (e.g., computer running web server). Hosts are also referred to as end devices.
- *Routers*: can forward IP packets to other devices. Routers are also referred to as intermediate devices (along with most layer 2 devices).

A network also often has devices which have a dedicated role, e.g., firewalls, web servers, DNS servers. The role is independent of the devices type. That is, a host may be a firewall, as may a router. And while web servers often run on hosts, they may also run on a router. And devices may have multiple roles, e.g., a router may be a firewall and DNS server.

From now on we will refer to devices as either: layer 2 devices, host and routers. 

Devices are connected via links. We are not going to distinguish between the type of links (wireless, Ethernet, optical fibre) at this stage. They are all just links.

Devices have *interfaces* which can be used to connect to a link. Interfaces are also called or directly associated with ports, (network) adapters, and (network interface) cards. We will often see *if* be used as an abbreviation of interface. An example is a computer that has two ports to plug two LAN cables into: that computer has two interfaces (and maybe even more, e.g., for WiFi).

### Hardware and IP Addresses

Layer 2 communication occurs between devices using *hardware addresses*. A hardware address is often also called a MAC address, physical address, layer 2 address, or data link layer address. Hardware addresses are assigned per interface. We will assume one interface can have one hardware address. Often hardware addresses are assigned to the interface hardware by the manufacturer, and never change.

Layer 3 communication occurs between devices using *IP addresses* (also called network address, internet address, layer 3 address). IP addresses are assigned per interface, usually by the network administrator (you). 

There are two versions of IP: IPv4 and IPv6. We are focussing only on IPv4 as it is still very common (and a little bit easier to start with for a beginner). 

This simplified model of a computer network is sufficient to get started with configuring networks in Linux. But in reality, computer networks are more complex than what is described here, and there are many exceptions as well as  cases where this model is not correct. However it is sufficient for now. 

We assume you know the above computer networking concepts, e.g., the role of switches and routers, structure of IP addresses, how IP forwarding and routing works. 







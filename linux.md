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

Devices have *interfaces* which can be used to connect to a link. Interfaces are also called or directly associated with ports, (network) adapters, and (network interface) cards. We will often see *if* or *dev* used to refer to an interface (device). An example is a computer that has two ports to plug two LAN cables into: that computer has two interfaces (and maybe even more, e.g., for WiFi).

### Hardware and IP Addresses

Layer 2 communication occurs between devices using *hardware addresses*. A hardware address is often also called a MAC address, physical address, layer 2 address, or data link layer address. Hardware addresses are assigned per interface. We will assume one interface can have one hardware address. Often hardware addresses are assigned to the interface hardware by the manufacturer, and never change.

Layer 3 communication occurs between devices using *IP addresses* (also called network address, internet address, layer 3 address). IP addresses are assigned per interface, usually by the network administrator (you). 

There are two versions of IP: IPv4 and IPv6. We are focussing only on IPv4 as it is still very common (and a little bit easier to start with for a beginner). 

This simplified model of a computer network is sufficient to get started with configuring networks in Linux. But in reality, computer networks are more complex than what is described here, and there are many exceptions as well as  cases where this model is not correct. However it is sufficient for now. 

We assume you know the above computer networking concepts, e.g., the role of switches and routers, structure of IP addresses, how IP forwarding and routing works. 

## Hosts, Routers and Interfaces in Linux

In Linux, all computers can generally be either a host or router. It is a small configuration change to switch between host and router, specifically, enabling/disabling IP forwarding. 

We will assume each host and router has 1 or more physical network adapters, and each adapter is assigned an interface name in Linux. Interfaces are often named based on the type of network technology and the number of the adapter in the computer. As Ethernet is widely used, you will commonly see interfaces called: ``eth0``, ``eth1``, ``eth2`` and so on. However another naming scheme is ``enp0s0``, ``enp0s1``, ``enp1s0``, and so on. For wireless adapters, interfaces may be ``wl0``, ``wlo1``, ``wifi2`` and similar. Other interface names you may come across include: ``lo``, ``vboxnet0``, ``tun2``, ``br`` (loopback, VirtualBox network, tunnel, bridge). Interfaces are assigned to network adapter devices, so ``dev`` is used to refer to an interface in many commands.

## ip: viewing and setting networking configuration

The ``ip`` command is used for viewing and setting networking configurations, usually applied to interfaces on a host or router. The command has multiple objects to operate on, and supports various options. To see them, simply run ``ip`` or view the man(ual) page (in Linux with ``man ip`` or searching online). Here we show selected ``ip`` commands to get started. We show the command via examples. You will need to change values, e.g., the actual IP address or interface name must be specified.

### Addressing

View your IP addresses (and other information) for each interface:

```bash
ip address show
```

Set the IP address for a specific interface (example with IP 1.1.1.1 with network mask /24 and applied to interface device ``eth0``):

```bash
ip address add 1.1.1.1/24 dev eth0
```

### Links

The interface connects to a link. You can use the link object to turn an interface on or off, which is referred to as up or down.

Turn an interface off (down):

```bash
ip link set eth0 down
```

Turn an interface on (up):

```bash
ip link set eth0 up
```

### ARP and Neighbours

ARP is used automatically by Linux computers to find the hardware address of neighbours on the same subnet. While we do not normally need to get involved in the ARP process, it is useful to view current ARP table:

```bash
ip neigh show
```

You will often be interested in the: IP address, interface, hardware address and state (such as REACHABLE, STALE or INCOMPLETE).

### Routes

View the routing table of your Linux computer:

```bash
ip route show
```

Add a default route via router 1.1.1.1 using interface eth0:

```bash
ip route add default via 1.1.1.1 dev eth0
```

Add a route to a specific subnet (3.3.3.0/24) via router 1.1.1.1 using interface eth0:

```bash
ip route add 3.3.3.0/24 via 1.1.1.1 dev eth0
``` 


## ping: testing network communications

## nc: testing application communications









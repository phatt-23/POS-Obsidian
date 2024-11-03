---
aliases:
  - IP address
  - address
  - MAC address
  - MAC addresing
  - IP adressing
---
- each protocol has different set of addresses
	- originally each separate HW technology had a different set and lenght of addresses 
		- unmaintainable, communcation with other HW was difficult or not possible
	- a need for standardization of addressing of LAN technologies
		- IEEE created [[MAC Sub-Layer|MAC addresses]]
			- 48-bit long - can be depleted in the future - newer standards already created
			- sometimes you might encounter Service Access Point (SAP) addressing on the [[LLC Sub-Layer]] (8-bit long)
			- [[Virtual LAN|Virtual LANs]] have their own VLAN ID, which could be considered an address

# IPv4 Addressing
- 32-bit long addresses
- every L3-aware ([[Network Layer]]) network interface has to have its own IP address
	- these are network interfaces of stations (hosts) and routers

- address division:
	- network prefix (network address part) 
		- is same for all stations (hosts) in the same broadcast domain (also called LAN segment)
		- routers use these addresses for routing
			- storing these addresses in their routing tables (limited size)
				- they don't have to keep track of all station addresses
				- only storing addresses of individual networks
	- node/host address part

## IP Addresses Allocation
- allocated by the Regional Internet Registry (RIR)
	- Europe's RIR is called RIPE (Réseaux IP Européens Network Coordination Centre)
	- electronic request form - mediated by ISP
- originally addresses were allocated regardless of the geographical location
- later established: 
	- hierarchical addressing
	- and allocation of network prefixes variable lengths (only what's needed, not wasting space like class IP addressing)
		- network prefixes can then be subnetted again
- private networks may utilize address ranges reserved for private use
	- has to avoid leaking such addresses to the Internet
	- 10.0.0.0/8, 
	- 172.16.0.0/12 (172.16.\* - 172.31.\*),
	- 192.168.0.0/16 - common for private networks connecting to the Internet through NAT (Netwok Address Translation)
	- 169.254.0.0/16

## Classes of IP addreses
- method for allocating addresses of the past, not being used anymore
	- with no regard for the future, wasting shit ton of unique addresses (fixed size network and host address parts)

![[classes_of_ip_addresses.png.png]]

- address space subdivided into 5 classes (A,B,C,D,E)
	- each beginnig with a certain sequence of bits
		- **A** (0), **B** (10), **C** (110), **D** (1110), **E** (1111)
			- class D addresses are still operational 
$$ 1110000_b = 128_D + 64_D + 32_D = 224_D $$
	- having network prefix following after this sequence


## Classless Addressing
- network prefix of arbitrary length can be allocated
	- has be accompanied by a *subnet mask* that specifies length of the network prefix
	- standardized as Classless Inter-Domain Routing (CIDR)
		- CIDR notation - slash behind an IP address (192.168.100.0/24)

## Special IP Addresses

![[ip_special_addresses.png.png]]

- this host - station pinging 0.0.0.0 is pinging itself
- universal broadcast (255.255.255.255) - sends packet to all stations in the on same LAN (broadcast domain)
- multicast - from 224.x.x.x to 239.x.x.x 
	- remnants from class addressing, class D
- reserved addresses (shall not be used on clients):
	- network address of the local network (all 0s in the host part of the IP address)
	- broadcast address of the local network (all 1s)

## Subnetting
- allows dividing network prefix between mulitple LAN segments
	- every segment is given a unique subnet address
	- segments can potentially have different number of stations
		- reserved addresses and router interfaces have to be taken into account
- the part in the **IP address originally allocated for hosts** (specification of nodes, host part of the address) is further *divided* into:
	- **subnet** ID
	- and **host** (node) ID
- the address (host part) may be split at any bit position according to the number of required network stations

![[subnet_mask.png.png]]

- subnet mask:
	- specifies how many bits of the subnetted address represent the network address + the subnet address
	- binary one at the particular indicates that the bit in IP address belongs to network + subnet address
- practical usage of subnetting:
	- used for determing the maximum address prefix length to request from your ISP that will provide enough IP addresses to cover the required number of network segments, with sufficient addresses for the devices on each segment
	- division of already given network prefix into a chosen number of segments
	- used in WAN addressing plans - connects LANs together creating a mesh

### Addressing Constant Subnet Mask
- not used anymore, was replaced by VLSM (Variable Length Subnet Mask)
- ![[constant_subnet_mask_1.png.png]]
![[constant_subnet_mask_2.png.png]]


# IPv6 Addressing
- 128-bit long addresses (16 bytes)
- written as hexadecimal numbers:
$$FEDC:\textbf{0}A98:7654:1230:\textbf{0000}:\textbf{0000}:7546:3210$$
	- leading zeros in each block may be omitted
$$FEDC:A98:7654:1230::7546:3210$$
	- no broadcasts (only multicasts)
	- introduction of anycast
	
	**Anycast** is a network [addressing](https://en.wikipedia.org/wiki/Addressing "Addressing") and [routing](https://en.wikipedia.org/wiki/Routing "Routing") methodology in which a single [IP address](https://en.wikipedia.org/wiki/IP_address "IP address") is shared by devices (generally servers) in multiple locations. [Routers](https://en.wikipedia.org/wiki/Router_(computing) "Router (computing)") direct packets addressed to this destination to the location nearest the sender, using their normal [decision-making algorithms](https://en.wikipedia.org/wiki/Routing_algorithms "Routing algorithms"), typically the lowest number of [BGP](https://en.wikipedia.org/wiki/Border_gateway_protocol "Border gateway protocol") [network hops](https://en.wikipedia.org/wiki/Hop_(networking) "Hop (networking)"). Anycast routing is widely used by [content delivery networks](https://en.wikipedia.org/wiki/Content_delivery_network "Content delivery network") such as web and [name servers](https://en.wikipedia.org/wiki/Name_server "Name server"), to bring their content closer to end users.

- global and link addresses
- StateLess Address AutoConfiguration (SLAAC)
	- routers adverise the local network address prefix
	- station append their MAC addresses (with some adjustments)
	- DHCPv6 (Dynamic Host Configuration Protocol) may be used for extra features

## IPv6 Subnetting
- hierarchical addressing scheme
- you will be given a prefix which is typically a multiple of 4 bits (nibble)
- typically /32 are allocated by RIRs (Regional Internet Registry) to organizations
	- if the organization is LIR (Local Internet Registry) 
		- their client is allocated /48 prefix which LIR subnets
			- end segments typically have /64 subnet mask
				- /65, /66, /67, ... masks are theoretically possible but SLAAC will not function
				- sometimes single address /126, /127, /128 masks are used, although they are discouraged because of potential issues with routers

# Port Number Addressing
- addressing of services (processes) on end systems
- the [[Tranport Layer|transport-layer]] entities providing some services are identified by:
	- the IP address of the machine they run on
	- port number 
		- is local to the particular machine
		- 16-bit long (0 - 65535), separate for UDP and TCP protocols
> While UDP and TCP share the same port number range (0–65535), each protocol maintains its own set of ports. This means that TCP port 80, for example, is different and independent from UDP port 80. A server can use the same port number for both TCP and UDP without conflict because they are managed independently within each protocol's stack.
- well known services (0 - 1023)
- other registered applications (1024 - 4096)
- other ports are client ports often assigned by the OS to the application
- *NOTE: both destination and source port are used to identify the flow*





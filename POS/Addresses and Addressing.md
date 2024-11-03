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

# IP Addressing
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

## Classes of IP addreses
- method for allocating addresses of the past, not being used anymore
	- with no regard for the future, wasting shit ton of unique addresses (fixed size network and host address parts)

![[classes_of_ip_addresses.png.png]]

- address space subdivided into 5 classes (A,B,C,D,E)
	- each beginnig with a certain sequence of bits
		- A (0), B (10), C (110), D (1110), E (1111)
	- having network prefix following after this sequence


## Classless Addressing
- network prefix of arbitrary length can be allocated
	- has be accompanied by a *subnet mask* that specifies length of the network prefix
	- standardized as Classless Inter-Domain Routing (CIDR)
		- CIDR notation - slash behind an IP address (192.168.100.0/24)





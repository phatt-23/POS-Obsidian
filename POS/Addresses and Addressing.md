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






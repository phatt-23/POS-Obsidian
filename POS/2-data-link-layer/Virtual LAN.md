---
aliases:
  - VLAN
---

- single physical switch can be divided into many logical switches (virtual switches)
	- a virtual local area network can be constucted thanks to this property
		- just by software configuration, no cabling changes needed
	- switch ports can operate in different modes:
		- access mode
		- trunk mode
- helps to separate 
	- traffic types (voice, video, ...) 
	- and users (admins, emplyee, guests, ...) on the same physical topology
- advantages:
	- network segmentation - smaller broadcast domains -> less processing of uncorrelated communication
	- increased security
- other applications:
	- router-on-the-stick - routing between VLANs
	- trunk link to server with VLAN-capable NIC
![[server_vlan.png.png]]
![[router_on_the_stick.png.png]]
## Access Link Port
- are normal non-trunk links
- a port belongs to only one VLAN
## Trunk Link Port
- carry traffic of multiple VLANs
- allowed VLANs on the trunk link can be configured
- frames traveling through trunk link have IEEE 802.1q tag inserted into the header
	- is used to differentiate traffic from different VLANs
	- VLAN ID is specified
	- presence of this tag is indicated by a dedicated EtherType field
	- whenever a frame is forwarded through a non-trunk link the tag is removed
- trunk links can be seen between: 
	- switches
	- switch and a router - inter-VLANs routing (router-on-the-stick)
	- switch and VLAN-capable server NIC

# VLAN Membership (extra)
- assignmet of stations to VLANs can be:
	- static - most common
	- dynamic 
		- according to MAC addresses, Layer 3 protocol, etc.
		- switches ask VMPS (VLAN Membership Server) for a station-to-VLAN membership when they new MAC address on port with dynamic VLAN configured
	
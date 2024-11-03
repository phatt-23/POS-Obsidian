- network protocols used in the Internet (also intranets, private networks)
- TCP (Transport Control Protocol) 
	- transport layer (4) protocol, 
	- used together with UDP (User Datagram Protocol)
- IP (Internet Protocol) 
	- network layer (3) protocol

#### Comparison of TCP/IP and OSI-RM stacks

![[tcp_ip_comp_osi_rm.png.png]]

#### Protocols of TCP/IP

![[protocols_of_tcp_ip.png.png]]

# IP - Internet Procotol
- operates in OSI Layer 3
- allows to send independent packets between stations of the internetwork
- is a unreliable connectionless service
	- doesn't care if the packet came, it's not its concern, its the concern of the upper layers
- version 4 (IPv4) is still widely used, transition to version 6 (IPv6) is ongoing

![[Pasted image 20241103184536.png|IPv4 header]]

## Packet Fragmentation
- applied when the packet has to be routed over a link with insufficient maximum unit length (Maximum Transfer Unit, MTU)
- either done by:
	- the source station 
	- or any router - only with IPv4 packets, for IPv6 packets it is not permitted to do so, instead it sends a "Packet too big" ICMPv6 message back to the sender
- the fragments are reassembled back into the packet at the destination
	- fragments may arrive out of order through various paths
	- fragments of each packet are indentified by the Identification (16-bit) field in the IP header (can be thought of as the some string indetifier)
	-  correct ordering is ensured by the Fragment Offset (13-bit) field (can be thought of as the index in a string data type)
	- last fragment is identified by the More Fragments flag in the Flags field
		- it is set to 1 if the fragment is not the last one
		- set to 0 if it is the last one
- the convention requires all Internet links to support MTUs of at least 576 bytes

# TCP/IP Supporting Protocols
- also called IP service protocols
- their purpose is to help the IP protocol do certain tasks it cannot do itself
- examples: 
	- ARP (Address Resolution Protocol), 
	- RARP (Reverse Address Resolution Protocol), 
	- ICMP (Internet Control Message Protocol), 
	- IGMP (Internet Group Management Protocol)

## ARP - Address Resolution Protocol
- used for when we don't know to which interface we should send the IP packet so it will arrive to the destination
- maps destination IP addresses to corresponding MAC addresses
	- ARP Request with an IP address in question are broadcasted when a corresponding MAC address is needed (is not known)
		- the learnt mappings of IP addreses and MAC addresses are put into ARP caches (table, similar to CAM tables in switches and routing)
- 



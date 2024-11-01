- includes methods of finding the shortest path
- forwaring of packets hop by hop along the shortest path (that is known to the router) through the network to the destination
- routing protocol - routing information exchange

# Router
- interconnects LANs at Layer 3 of OSI-RM (network layer) with different networking technologies (Wi-Fi, Ethernet, ...)
- contains a routing table
	- records of network addresses and ports (similar to the MAC table in switches)
	- may be configured: 
		- staticly - manual
		- dynamicaly - based on the informaton of the neighboring router
- routes packets of a particular network protocol
	- IPv4, IPv6, ...
- processes network headers of passing packets:
	- decreases *TTL* (Time To Live) field
		- protection against loops
	- recalculation of the checksum
	- processes options, etc.
	- according to the *Destination Address* (in the header of the incoming packet) searches the next-hop router
- additional functions:
	- firewall, IDS/IPS (Intrusion Detection and Prevention System)
	- NAT (Network Address Translation)
	- VPN Termination
	
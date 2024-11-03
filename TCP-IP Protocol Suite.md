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
- in IPv4 either the source station or any 










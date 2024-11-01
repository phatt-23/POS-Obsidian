[prez1-3](https://lms.vsb.cz/pluginfile.php/2310316/course/section/2805839/LAN-WAN-topologies.pdf)
### Local Area Networks and Wide Area Networks

- no real classification - today primarily by a geographical area they cover
- LAN
	- common shared channel 
	- only 1 packet on a medium at a time (in unswitched LANs)
	- high transfer rates (Mbps -> Gbps)
	- in modern LANs (switched) there are multiple packets in the tree structure
- WAN
	- partially meshed topology
	- multiple packtes may be present on a medium at same time
	- lower transfer rates (kbps)
	- modern WANs have high-speed link (1Gbps -> 10Gbps)
---
### Network Topologies
- general:
	- physical or logical arrangement and interconnection of network elements (nodes), which are computers and network devices
	- typically bound to a network technology used
		- Token Ring uses ring topology
		- Ethernet uses tree or bus structure
	- desired characteristics:
		- extensibility
		- resiliency
		- reconfigurability
		- overall throughput
- LAN topologies:
	- bus
		- passive medium
		- low to no delay
		- signal received by all nodes
		- limited security, capacity of the shared medium
		- poor resiliency against media failures - failure is hard to troubleshoot
	- star
		- tree topology with one root
		- nodes connected to a central hub (active or passive)
		- resilient against failure of nodes
		- failure of the hub is critical
	- tree
		- generalization of star, also called distributed star
		- most widely used nowdays
		- hierarchical control of media access
		- possibility of implementing redundant links
		- mustn't include loops, must stay acyclic
	- ring
		- ring of p2p unidiractional links
		- data circulates around the ring
- WAN topologies:
	- mesh
		- point-to-point links between routers
		- alternate paths may exist
		- full-mesh (complete graph) and hub-and-spoke (tire on a bike)
- Internet's topology
	- is a mixture of networks with various topologies
	- LANs with various topologies are interconnected via routers
---



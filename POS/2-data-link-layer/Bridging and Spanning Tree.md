![[broadcast_and_collision_domains.png.png]]
# Bridge
- operates at OSI RM layer 2
- bound to a single LAN network technology - same frame format on all interfaces
- two types: 
	- transparent  bridging (self-learning)
	- source-route bridging
- today bridges have been replaces by *switches*
- problem of *frame duplication* in looped topologies 
	- this problem is solved by the *Spanning Tree Protocol (STP)*


### Transparent Bridging
- frame forwarding according to bridging table 
	- set of records of (MAC_address, port)
	- record have limited lifetime 
		- are renewed when frame with corresponding MAC address arrives
- bridging table filled according to source MAC addresses and ports of incoming frames
- frames with unknown destination MAC address are flooded to all ports
- broadcast flooded to all other ports

### Source Route Bridging
- path through network is determined by the sender (source station)
- frames contain Routing Information Field (RIF)
	- a list of network segments/bridge IDs they have to travel through
- used in Token Ring
- before sender sends to a destination for a first time
	- it has to fetch the path leading to the destination
		- sends a route discovery frame
		- every bridge appens its ID to the RIF in discovery frame and forwards to all ports
		- after destination station receives the discovery frame
			- reverses the RIF and sends back to the source
	- source uses the discovered path in subseqeunt commucation

# Spanning Tree Protocol	

> (corny ass poem)
> I think that I shall never see. 
> A graph more lovely than a tree. 
> A tree whose crucial property 
> Is loop-free connectivity. 
> A tree that must be sure to span. 
> So packets can reach every LAN. 
> First, the root must be selected. 
> By ID, it is elected. 
> Least cost paths from root are traced. 
> In the tree, these paths are placed. 
> A mesh is made by folks like me, 
> Then bridges find a spanning tree.  — Radia Perlman

- algorithm implemented on bridges and switches (IEEE 802.1d)
- tree is continually spanned through the whole network topology
	- construction of acyclic graph - tree
	- if there are redundant links only one port may be operational 
		- others are blocked - in a tree no loops are permited
	- in case of failure - automatic recalculation of the tree - unblocking of blocked port(s)
- stages:
	- election of the tree root (root bridge)
		- based on configured priorities 
		- or factory-set bridge ID in case of equal priorities
	- creation of shortest path tree
		- from root to all other nodes
		- link preference influenced by link speed - faster will be chosen
	- reduntant ports are blocked
- root port (RP), designated port (DP), blocked port (BP)

![[spanning_tree.png.png]]

- operation in converged state:
	- root generates BPDU (Bridge Protocol Data Unit) message every 2 seconds
		- travels down the tree
	- every bridge check presence of BPDU on its root port
	- ports are categorized
		- blocking 
			- if it were active, it would cause a loop
			- BPDU is still received
			- may transition to forwarding mode if STP so determines	
		- listening - listening for BPDU, awaits information that would cause it to return to blocking state
		- learning - adding source addresses from frames to MAC table
		- forwarding - normal operation
		- disabled - administratively

- reconvergence (in case of failure) may take up to 50 seconds




- IEEE 802.2
- responsibilities of LLC:
	- defines services provided to upper layers irrespective of the LAN technology
		- provides a common software interface
		- abstracts away diffrences between individual LANs of the 802 project
	- allows addressing of entities (stations, routers) within the same network node by associating each protocol with a unique SAP
		- when a device receives a packet, the LLC uses the SAP to identify which upper-layer protocol should process it
			- SAPs are addresses within LLC that identify network services or protocols available on a device (such as IP or IPX)
			- this allows multiple protocols to coexist on the same physical network link by distinguishing data for each protocol through SAP identifiers
	- optional error control and flow control

### Implementation of LLC Sub-Layer
- unified LLC frame format is carried in different MAC frames
	- LLC sub-layer adds its header to the payload of the MAC frame
	- format and contents of the LLC header don't depend on the LAN technology belonging to the MAC sub-layer

### Services Provided by LLC Sub-Layer
- connectionless unackknowledged service
	- most common one, no flow control and error control
- connection-oriented service - logical connection between remote entities (through SAPs)
- connectionless acknowledge service

### Contents of the LLC Header
- placed at the beginning of data part in MAC layer frame
- DSAP and SSAP - Destination SAP (destination entity) and Source SAP (source entity)
- some other shit fuaaaaaaaaawk
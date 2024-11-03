- started in 1982 and is still ongoing
- its efforts are to standardize the current state of LAN technologies
	- resulted in standards that were accepted by ISO 
		- under the name ISO 8802 standard (1987)
	- standardizes the physical and link layer
		- higher layers implemented as software modules in LAN stations or routers in case of WAN

# Suite of IEEE 802 Recommendations

![[ieee_802_suite.png.png]]

## IEEE 802.1 Recommendation
- defines: 
	- mutual relationship between other standards 
	- common concepts for all LAN types
- [[Bridging and Spanning Tree|802.1d]] - bridging principles (transparent and source-route bridges) and Spanning Tree protocol
- [[Virtual LAN|802.1q]] - VLAN
- 802.1p - QoS (traffic prioritization)

# Relationship with OSI-RM
- IEEE 802 divides the data link layer into:
	- MAC (Media Access Control) sub-layer
		- different for various network technologies
	- LLC (Logical Link Control) sub-layer (IEEE 802.2)
		- unifies all of the various network technologies

![[data_link_layer_and_ieee.png.png]]

## MAC Sub-Layer
- MAC sub-layer standards for current LAN types:
	- 802.3 - CSMA/CD networks (Ethernet)
	- 802.4 - Token Bus
	- 802.5 - Token Ring
	- 802.11 - Wireless LAN (Wi-Fi)
	- 802.15 - Wireless PAN (Bluetooth)
	- ...
- responsibilities:
	- MAC access methods
	- frame format
	- station addressing (MAC addresses)
	- error detection

### MAC Addresses
- is assigned to each physical node in the network
- address length is 48 bits
	- 6 hexadecimal numbers separated by a semicolon
	- first byte holds special 2 bits:
		- lowest - unicast (0), group (1) addresses
		- 2nd lowest - globally unique (0), locally assigned (1)
	- global unique address:
		- first 3 octets are manufacturer's ID assigned by ISO
		- last 3 octets assigned by the manufacturer
- all bits set - broadcast - `FF:FF:FF:FF:FF:FF`
- all bits unset - for testing empty frames

### MAC Frames
- transmitted by octets to the medium starting with the leftmost octet
- order of bits in transmitted octets differs based on different MAC technologies used:
	- 802.3 Ethernet - LSB bit first
	- 802.5 Token Ring - MSB bit first

## LLC Sub-Layer
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
	- most common one, no flow control and r
- connection-oriented service - logical connection between remote entities (through SAPs)
- connectionless acknowledge service







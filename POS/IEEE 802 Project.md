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
	- LLC (Logical Link Control) sub-layer
		- unifies all of the various network technologies

![[data_link_layer_and_ieee.png.png]]

## MAC Sub-Layer
- MAC sub-layer standards for current LAN types:
	- 802.3 - CSMA/CD networks (half-duplex Ethernet)
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
-












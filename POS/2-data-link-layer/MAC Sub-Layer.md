- MAC sub-layer standards for current LAN types:
	- 802.3 - [[Probabilistic MAC Protocols|CSMA/CD]] networks (Ethernet)
	- 802.4 - Token Bus
	- 802.5 - Token Ring
	- 802.11 - Wireless LAN (Wi-Fi)
	- 802.15 - Wireless PAN (Bluetooth)
	- ...
- responsibilities:
	- [[Multiple Access Control and Protocols|MAC access methods]]
	- frame format
	- station addressing ([[Addresses and Addressing|MAC address]])
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



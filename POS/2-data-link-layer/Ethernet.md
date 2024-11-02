- originaly DIX Ethernet (DEC-Intel-Xerox, Ethernet II, 10Mbps) with no LLC sub-layer
	- operating half-duplex mode
- later standardized as IEEE 802.3
	- frame format changed - type/length field interpretation
	- Ethernet today is a whole technology suite with a common frame format

![[ethernet_used_technologies.png.png]]


## Ethernet Family Members Naming According to IEEE 802.3
     {Mbps|Gbps**G**} {Base|Broad} {segment length per 100 m|-medium}
- medium:
	- T, TX - twisted pair
	- F, FX, LX, SX - fiber optic, L is single-mode, S is multimode
- examples: 10Base5, 10Base-T, 100Base-LX10, 10GBase-T, ...

## Half-Duplex Ethernet
- uses p-Persistant CSMA/CD (a MAC protocol)
	- maximal signal delay is defined to be 51,2 microseconds
		- 2 times the maximum time of signal propagation + delays incured by repeaters
		- corresponds to 512 bit (64B) intervals at 10Mbps
		- implies the maximum cable lengths
	- station detecting a collision sends "jam" signal to inform other stations
	- exponential backoff applied after collision

## Full-Duplex Ethernet
- collision-free switched environment
- for compatibility with half-duplex NICs, P2P links can also operate in half-duplex mode

## Duplex and Speed Autonegotiation
[wiki](https://en.wikipedia.org/wiki/Autonegotiation?useskin=vector)
- stations may automatically negotiate duplex-mode and speed
- implemented using Fast Link Pulses (FLP)
	- each side shares its capabilities by burst pulses, 
	- then the highest-performance transmission mode they both support is chosen

## Ethernet Frame Format
- type/length field



[prez1-2](https://lms.vsb.cz/pluginfile.php/2310316/course/section/2805839/media.pdf)
### Types 
- copper 
	- coaxial, 
	- twisted pair (shielded, unshielded)
- optical
- wireless
#### Coaxial
- usage options: 
	- BaseBand (no modulation, units of 100m...1km)
	- BroadBand (modulated signal, 1km...)
- components: crimp connectors, T-connectors, terminators
#### Twisted Pair
- cheaper than coaxial
- worse parameters than coaxial
- 4 twisted pairs, the pairs are also twisted
- usage: LAN in baseband (100m for 1Gbps)
- TP category determines quality
- shielding:
	- prevents electromagnetic interference
	- applied to individual pairs or the collection of pairs 
	- need to be grounded at both ends
	- must sustain shielding all the way through between devices
- EIA/TIA-568-TP Categories: (*Electronic Industries Alliance* a *Telecommuncations Industry Association*)
	- every category defines parameters up to the upper frequency
	- frequency increases each category
	- relates to cables as well as other components (patch-panels, connectors, jacks, ...)
	- parameters (measured) [wiki](https://en.wikipedia.org/wiki/Copper_cable_certification?useskin=vector):
		- propagation delay
		- delay skew
		- attenuation (also insertion loss)
		- return loss (also reflections) - amount of signal reflected back to transmitter
		- near/far end crosstalk (NEXT, FEXT)
		- DC loop resistance
	    (calculated) - ACR (Attenuation / Crosstalk Ratio)
	- *note: the frequency can be viewed as bits*

| Name  | Bandwidth       | Application                               | Notes                                                                                                  |
| ----- | --------------- | ----------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| Cat1  | 1 MHz           | non                                       | 1 Mbps, was never a standard                                                                           |
| Cat2  | 4 MHz (4Mbps)   | IBM Token Ring                            | never standard                                                                                         |
| Cat3  | 10 MHz (10Mbps) | 10Base-T                                  | telephone cables                                                                                       |
| Cat4  | 20 MHz          | 16Mbps, Token Ring                        | never widely installed                                                                                 |
| Cat5  | 100 MHz         | 100BaseTX, 100Base-T, (100Mbps Ethernet)  | FastEthernet                                                                                           |
| Cat5e | 100MHz          | 1000Base-T, 2.5GBase-T (100Mbps Ethernet) | new parameters - used for Gigabit Ethernet                                                             |
| Cat6  | 250 MHz         | 5GBase-T, 10GBase-T, (10Gbps Ethernet)    | limited cable length                                                                                   |
| Cat6a | 500 MHz         | 5GBase-T, 10GBase-T, (10Gbps Ethernet)    |                                                                                                        |
| Cat7  | 600 MHz         |                                           | individual pairs and whole cable shielded, used special connector GG45 (backward-compatible with RJ45) |
| Cat7a | 1 Ghz           |                                           | used for 40G / 100G Ethernet                                                                           |
| Cat8  | 2 GHz           | 25GBase-T, 40GBase-T                      | 35m maximum length, used in data centers                                                               |
- pairs used per Ethernet type:
	- GigabitEthernet connection (1 Gbps) uses all 4 pairs
	- FastEthernet connection (100 Mbps) uses only 2 pairs
#### Optical Fiber	
[more info](https://www.thefoa.org/tech/ref/basic/fiber.html)
- very high transfer rate (tens of Gbps, high bandwidth) and reachable distance
- resilient against noise and eavesdroping (signal tapping)
- works in: 
	- singlemode - small core diameter, one beam of light
	- multimode - larger core diameter, multiple beams
- numerical aperture - range of angles over which the system can accept the light
- limitations:
	- only 2-level data encoding - light and dark
	- the materials used (their Snell's index) in combinations with the light reflecting can cause dispersion -> causes deformation 
		- can be solved by using singlemode fibers
- consists of 2 fibers or more (incoming, outgoing)
- ideal for vertical mounting in structured cabling
- joining:
	- first cleave and leave the fiber core, then splice them together
	- mechanical or fusion splicers
- names of connectors: ST, SC, FC, LC, MT-RJ and others [wiki](http://en.wikipedia.org/wiki/Optical_fiber_connector)


## Structured Cabling
[more info](https://community.fs.com/article/horizontal-cabling-vs-backbone-cabling.html)
- today generic cabling is used, not bound to any specifications or ideology
- integrates various services - telephony, LAN, alarm system
- easily upgradable as the structure is general
- standards:
	- commercial building wiring standard - EIA/TIA 568 now ANSI/TIA-568-D
	- residential buildings - TIA 570-A-1998, now ANSI/TIA-570-D
	- defines common terminology, topology, cable types and lengths, connectors and other cabling components
- terminology:
	- horizontal 
		- connects telecommunication rooms to work areas and outlets on the floor
		- at least UTP Cat5e or Cat6a 
		- RJ45 connectors
		- maximum 100m cable lengths between active network devices
		- at least 2 outlets per 10m^2
		- network devices and stations are interconnected using patch cords and patch panels
	- vertical (backbone) cabling 
		- connects the equipment rooms and telecommunication roots
		- optical cabling is preferred
	- telecommunication closet/room - contains telecom. equipment that connects backbone cabling and horizontal cabling subsystems
	- main crosspoint frame (MCF)
	- intermediate distribution crosspoint frame (ICF)
	- point of presence (POP)
		- demaracation point between the building and the connection provider

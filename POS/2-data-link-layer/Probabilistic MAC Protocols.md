- collision slot (only concept, not a protocol)
	- maximum theoretical time for a frame to travel a network 
		- during which we can't transfer data
		- time is wasted

# ALOHA System
- it is necessary to control the behaviour of this method
	- by cleverly modifying its parameters
		- packet transmission rate 
			- regulated by the current load
			- higher transmission rate results in faster transfers
			- but has to be limited if the channel begins to block
		- exponential backoff (using heuristics)
			- exponentially lowers the transmission rate as failures grow
- still in use in *wireless networks* and *communication over satellites*
	- long propagation delay doesn't allow efficienct checking before transmission

### Pure Aloha
- transmitter doesn't check, just starts
- collision detection - packet acknowledgement failed to receive in timeout
	- packet retransmitted after timeout
	- random pauses to avoid global synchronization of multiple transmitters
- max. channel capacity is 18.4%

### Slotted Aloha
- trasmitter can only start in a particular golbally synchronized time instants (timeslots)
- transmission will succeed if only one packet was transmitted in a timeslot
- less collisions - max. channel capacity is 37% 

# Carrier Sense Multiple Access (CSMA)
- group of multiple access methods/protocols
- listening to the carrier signal present on the channel
	- detects if it's busy
- typical for wired LANs
- necessary assumtions are:
	- stations can hear each other well
	- low signal propagation delay
- if assumptions are not met, then CSMA protocols performs worse than ALOHA

### 1-Persistent CSMA
- channel checked before transmission
- if busy then trasmissin is deffered until the previous finishes
	- sensing the medium continually
	- risk that multiple transmitters are waiting at the same time	
- if collision is detected then the transmitter waits for a random time
	- avoiding global synchronization

### Non-Persistent CSMA
- if channel is busy, transmitter waits for random time before cheking again
- reduces risk from 1-Persistent CSMA, where multiple transmitters are waiting
- wastes time by underutilization of the channel

### p-Persistent CSMA
- waits for free medium
	- checking continually
- after idle medium is detected - transmitter will transmit with probability *p* or waits one timeslot (propability *1 - p*)
	- timeslot period is 2x maximum propagation delay
- if after waiting transmitter detects that the channel is busy it waits again	
- utilization of the channel is optimized by choosing right *p* probability parameter
- if *p = 1* then behaves the same as 1-Persistent CSMA
- if *p << 1* then there are almost no collisions but the avg packet delivery time grows rapidly

### CSMA/CD (CSMA with Collision Detection)
- special case of Persistent CSMA
- before transmission the medium must be idle for a duration of the collision slot
- station detects collision by listening to the signal on the medium during its own transmission
	- if collision detected then the transmission is abrubtly stopped
		- avoids wasting channel capacity with unusable corrupted packets
	- ensures faster and more reliable collision detection
		- the station that detects a collision sends a special collision "jam" signal
	- all stations whose transmission collided have to wait for a random time
		- using backoff algorithm
- used by *Ethernet*
- timing - close relation between:
	- velocity of signal propagation on the medium
	- maximum allowed length of cable segment
	- minimum time of frame transmission duration - thus mimum frame length











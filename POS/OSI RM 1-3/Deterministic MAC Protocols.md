- general classification
	- centralized control
	- distributed control

# Centralized Control
- master (central) station dedicated to assign the capacity of the channel to the slave (slave) stations
- introduces single point of failure

### Centralized Control Polling
- master polls the slaves (offers the right to transmit)
- polled slave (station) either: 
	- sends the data frame
	- or informs there are no data
	- or remains silent
- round-robin polling scheme
- inefficient for large number of stations (slaves) and light unbalanced load
### Centralized Control Request Arbitration
- *note*: to arbitrate -> rozhodnout, rozsuzovat
- slaves use separate (narrow-band) channels to ask for access to the data channel
- master arbitrates the requests and assigns the channel to a slave

# Distributed Control
- independent of a single central control station
- implementations tends to be more complicated

### Distributed Control Bit-Map Protocol
[more info](https://www.tutorialspoint.com/bit-map-protocol)
- master periodically generates reservation frame
	- *n* bits long each representing a timeslot, because there *n* stations
	- if *k-th* station wishes to transmit it sets the its *k-th* bit in reservation frame
		- it announces itself to the master that it wishes to transmit
- master assigns the right to transmit to one station
	- generally in order of time slots
- if there are no bits set, an empty reservation frame still repeats
- efficiency of $O(n)$
### Distributed Control Binary Countdown
- slaves are given binary addresses
- before transmission they have to send its address to the master bit by bit
- bits transmitted by different station are logically OR-ed
- if the station sends 0 but hears 1
	- it refrains from the transmission as another station with higher priority wants to send data
	- stations may be given priorities uring the addressing scheme
	- to avoid a monopol - addresses can be rotated between stations
- only the station that successfully transmitted its full address can send a frame
- necessary sychronization to define the instants when stations may start with their address transmission
- efficieny of $O(\log_2{n})$

### Distributed Control Adaptive Tree-Walk Protocol
[more info](https://www.tutorialspoint.com/the-adaptive-tree-walk-protocol)
- stations are leaves of a binary tree
- DFS (Depth First Search) is applied to find a subtree with just one station that wants to send data
	- at the beginning - root - all stations can transmit
	- if collision occurs the left and right branches are recursively searched 
	- after data frame was sent without collision a slot is reserved (there is a timeslot potentially reserved for every station)
### Distributed Control Token Passing
- right to transmit is represented by holding a token
	- station may hold for a only limited time
- token is passed around
	- stations have to know threir addresses and the successor's address
- necessary mechanisms:
	- ring initializing - station learn their successor
	- attachement and detachement of station to/from the ring
	- handling token loss/duplication





















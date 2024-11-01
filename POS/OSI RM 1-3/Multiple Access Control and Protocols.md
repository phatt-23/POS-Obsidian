- the medium (or its sub-channel) could be sharedd by multiple stations
	- only one can transmit at a time, otherwise traffic collides and data is corrupted
	- all stations must agree which one is allowed to transmit
- for this purpose multiple access control (aka MAC) protocols have been developed
### Classification of MAC Protocols
- [[Deterministic MAC Protocols]] (contention-free, distributed algorithm)
	- defines a sequence in that the stations may transmit
	- more than one station will never access the medium at the same time
	- a portion of the channel capacity is consumed by the MAC protocol
- [[Probabilistic MAC Protocols]] (contention, non-deterministic, probabilistic algorithm)
	 - used to determine which station will be allowed to transmit next
		- random waiting times
	- multiple stations trying to transmit at the same time may result in a collision
	- the access control method has to deal with collisions 
		- tries to minimize the probability of a collision
- comparison of deterministic and non-deterministic (probabilistic) methods:

| deterministic                            | non-deterministic                 |
| ---------------------------------------- | --------------------------------- |
| more suitable for heavy traffic networks | suitable for low traffic networks |
| overhead in MAC algorithm                | simpler MAC algorithm             |










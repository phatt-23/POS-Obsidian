# Communication
- two basic approaches to communication:
	- connection-oriented communication
	- conntectionless communication

## Connection-Oriented Communication
- communication session established before data transfer
	- memory allocation for both endpoints and intermidiaries
	- stateful - scalability problem
- delivers data streams in the same order as it has been sent

- implementation based on the level where its implemented:
	- network technology level
		- before transmission - allocate circuit between the trasmitter and receiver, intermediaries have to also allocate resources
		- after transmission - tear down after finishing
	- transmitter/receiver protocol level
		-  implementation on the software level
		- connection is represented by the current state on the transmitter and reciever
		- underlying technology (network) can either be connection-oriented or connectionless


## Connectionless Communication
- message sent from transmitter to any receiver without any prior agreement
- messages treated by the network as independent entities
	- may be received out of order or be lost
- stateless - no state information is needed


# Layered Communcation Subsystem Architecture

![[layered_communcation_practicaly.png.png]]

- decomposes big concerns during communication into smaller sub-systems
	- easier to implement, separation of concerns, more modular - scalable
	- well defined interfaces - Service Access Points and Primitives (similar to APIs) 

![[comm_interfaces_between_layers_and_p2p_protocols.png.png]]

- peer-to-peer protocols:
	- define rules of cooperation between entities of the same layer at different systems
	![[p2p_protocol.png.png]]

- service provider entitiy:
	- a layer consists of one or more entities that provide and implement services of the layer
	- each entity can use the services provided by entities in the layer below
	- entities communicate with entities of the same layer

- service access point
	- defines rules of communication between adjacent layers (layers below and above)
	- it's a software interface - it's provided operations are called *service primitives*:
		- these are used by the service user and are provided by service provider
		- abstrace operations - no implementation definition exists
		- types:
			- request - service user's request for a particular service from the lower layer
			- confirm - confirmation of the service to service user in the upper layer
			- indication - information of the service user about the occurence of an event
			- response - response of the service provider to the indication from the service user

![[service_providers_and_access_points.png.png]]

![[service_access_points.png.png]]


## Layered Communcation Terminology
- information to be passed to peer entity is exchanged between layers through Service Access Points (SAPs) as Service Data Unit (SDUs)
	- SDU is accompanied with Interface Control Information (ICI)
		- provides further information about the SDU for the lower layer
- P2P protocol exchanges Protocol Data Units (PDUs):
	- PDU contains:
		- payload from the upper layer and 
		- Protocol Control Information (PCI) (header/trailer)
	- every layer treats PDUs passed down from the upper layer as SDU and adds its own headers/trailers (control information)

![[pdu_sdu_relationship.png.png]]

*note: IDU stands for Interface Data Unit*

![[encapsulation_in_practice.png.png]]

# ISO/OSI Reference Model
- system 
	- standalone unit capable of processing information and commication with other systems
- open 
	- specifications of its architecture are publicly available
	- all system suiting the specifications are inter-operable
- ISO/OSI-RM: 
	- treats the open system as an abstract model of the real open system
		- particular implemtations are not prescribed
	- general model of the open system interconnection
		- using layered communication subsystem architecture
	- specifies general responsibilities of individual layers
		- services provided to the layer above and services expected from the layer below
	- goal was to provide a common framework to standardize of networking subsystems of the interconnected systems
	- today used as a layering scheme and a terminology standard
- layers of OSI/ISO-RM:
	1) Physical Layer
	2) Data Link Layer
	3) Network Layer
	4) Tranport Layer
	5) Session Layer
	6) Presentation Layer
	7) Application Layer

## Physical Layer
- takes care of physical bit stream transfer between neighboring systems
	- point-to-point or multi-point connections
	- full-duplex or half-duplex modes of operation
- defines interaction of a single device with the physical medium
	- physical and electrical parameters of the medium interface
	- exact specifications about how are data represented on the medium
		- signal levels, data encoding, data modulation
- can include media access control (MAC, typically on layer 2)
- services to the upper layer:
	- transmission of raw bit streams
	- physical connection establishment and termination
- examples: RS232, Ethernet 10Base-T, Ethernet 100Base-TX	

## Data Link Layer
- provides one or more logical connections for network layer entities on neighboring systems
- services provided to upper layer:
	- formatting and recognition of data frames
	- addressing and identification of communication participants
	- error detection and correction, error indication
	- estalishment, maintanance and termination of logical connections
	- flow control
- is often split into two sub-layers:
	- Logical Link Control (LLC) - unifies handling of various network technologies used with different MAC
	- Media Access Control (MAC)
- examples: 





























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
	1) [[Physical Layer]]
	2) [Data Link Layer]([[Data Link Layer]])
	3) [Network Layer]([[Network Layer]])
	4) Tranport Layer
	5) Session Layer
	6) Presentation Layer
	7) Application Layer
	- each provides their own set of functions the layer above can use
		- some of which are common to more layers
			- error detection and correction
			- flow control
			- fragment and reassembly (of long messages)
			- mapping of sessions to lower layers (1:1, 1:n, n:1)


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
- examples: LLC 802.2, PPP (Peer-To-Peer Protocol), Frame Relay

## Network Layer
- allows: 
	- overcoming differences between various network technologies (together with LLC in layer 2) be it connection-oriented or connectionless technology
	- establish the universal service interface
- provides: 
	- means for data transfer between *non-neighboring* systems using intermediate systems
		- functions and protocols for hop-by-hop data transfer - *routing*
		- hides the network topology from the Transport Layer
	- *unique system addressing* in scope of the whole internetwork
- services provided to the upper layer:
	- connection-oriented network service - X.25
	- connectionless network service - IP, IPX
- examples: IP (Internet Protocol), IPX, X.25

## Transport Layer
- provides tranparent (reliable) data transfer between two entities in the transport layer (end users)
- establishes addressing of transport-layer entities in scope of a device with a single network address
	- multiple transport session may exists between two systems in parallel
	- allows multiplexing of multiple connections with a single virtual circuit
- takes care of: 
	- segmentation and reassembly
	- error correction
	- flow control
- services provided to the upper layer:
	- connection-oriented services - TCP (Transport Control Protocol)
	- connectionless services - UDP (User Datagram Protocol)
- stands between the network infrastructure and end-systems that use it
	- transport session is established directly between end-system transport entities
	- intermediate systems don't participate
- examples: TCP (Transport Control Protocol), UDP (User Datagram Protocol)

## Session Layer
[glossary](https://nordvpn.com/cybersecurity/glossary/session-layer/)
- organizes and synchronizes the dialog between peer entities of presentation layer
- services provided to the upper layer:
	- dialog control 
		- simplex (one-way), 
		- half-duplex (alternating) 
		- or duplex communication (both way)
	- flow control
	- message transfer mode - normal, urgent or delayed
	- checkpoints
	- multiplexing and demultiplexing of an application session to one or multiple transport layer sessions 
- examples: 
	- RPC (Remote Procedure Call)
	- sharing of local disks, printers
- difference with Transport Layer:
	- transport-layer sessions are established only for the duration of a particular data transfer
	- session-layer sessions are exist for the whole duration of the remote communication
		- being logged-in in VSB SSO Network for a certain time before being signed out (Edison, LMS, Roundcube)

## Presentation Layer
- unifies how informatoin passed between application-layer entites is represented
	- binary representation of data types and characters
- provides a mechanism for agreement of message syntax
- deals only with the structure of passed messages
	- semantics are only known to the application layer
- functions of the layer:
	- appointment of the message syntax (that why this layer is also called Syntax Layer)
	- data translation:
		- on the sender's system it ensures that data is transformed in a way that is readable (conforms to a common format) for the receiving systems 
		- receiver translates the received data

_The presentation layer ensures the information that the application layer of one system sends out is readable by the application layer of another system. On the sending system it is responsible for conversion to standard, transmittable formats. On the receiving system it is responsible for the translation, formatting, and delivery of information for processing or display. In theory, it relieves application layer protocols of concern regarding syntactical differences in data representation within the end-user systems. An example of a presentation service would be the conversion of an extended binary coded decimal interchange code (EBCDIC-coded) text computer file to an ASCII-coded file. If necessary, the presentation layer might be able to translate between multiple data formats using a common format._ [wiki source](https://en.wikipedia.org/wiki/Presentation_layer?useskin=vector)

- examples: 
	- specifications of character (string) and image representations:
		- ASCII/EDDIC, TIFF/JPEG/...
	- specifications binary data representations:
		- XDR, CDR/GIOP, ASN.1+BER
	- bit and byte ordering
	- data encryption (can also be done by other layers)
	- data compresion

## Aplication Layer
- provides access to the communication subsystem to application programs
- specifies format in which application programs have to provide/accept data
- services provided:
	- determination of identity and availability of the communication partner
	- appointment of functions required from lower layers (dictates)
		- specificatin of the necessary Quality of Services (QoS)
		- determining resource availibility
		- selection of diaglog mode
		- specification of the responsibilities concerning error detection and correction and data consistency
		- agreement of the message syntax
- examples:
	- network applications - e-mail, file transfer, ...
	- any application software with some networking enabled (command in terminal, GUI apps, ...)

# Common Protocol Data Unit Names of Individual Layers
- common names:
	- *messages* - Application, Presentation, Session Layers 
	- *segments* (TCP), *datagrams* (UDP) - Transport Layer
	- *packets* - Network Layer
	- *frames* - Data Link Layer
- this doesn't mean they can't be reffered to under different name



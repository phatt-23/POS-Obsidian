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
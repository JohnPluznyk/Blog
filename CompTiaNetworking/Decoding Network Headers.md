	- when data is being sent out it is being **ENNCAPSULATED**
	- when data is coming in it is being **DECAPSULATED**

	- when we are encapsulating we are building PDUs (Protocol Data Units)
	- when we are decapsulating we are tearing apart PDUs

## Encapsulation example for requesting a web page
### 7 Application
 - First, we would ask ourselves what protocol would we use to request a web page from said server/node? **HTTPs**.  "HTTPs" would be the protocol
 - **HTTPs** will format/encrypt the data during the **PRESENTATION LAYER (L6)**
### 4 Transport / Segment / Datagram
- We are adding on the L4 header "transport layer header"
- we encapsulate the data and add the L4 header
- The PDU is now called a "segment" or "datagram"
- The "L4 header" or "transport layer header" for a **TCP/segment (reliable)** contains the following information
	- source port
	- destination port
	- sequence number
	- acknowledgement number
	- header length
	- reserved
	- flags
	- window size
	- TCP checksum
	- urgent pointer
- **The source and destination port information is taken from the Application layer**

- The "L4 header" for a UDP/Datagram (unreliable) contains the following:
	- 16-Bit source port
	- 16-Bit destination port
	- 16-Bit UDP length
	- 16-Bit UDP checksum
### 3 Network / Packets
- When adding on the L3 header, the PDU is called a "PACKET"
- Depending on which version of IP you are using (IPv4, IPv6) will determine how your Layer 3 header / packet looks

- **IPv4**
	- version
	- IHL
	- service type - "Quality of Service"
	- total length
	- identification
	- flag
	- fragment offset
	- TTL (Time To Live) - maximum age of packe - determined by the O.S. of sender
		- Maximum number of hops left
	- Protocol - refers to what is happening at the Upper Layer Header
		- What protocol are we using "HTTPs", "smtp", "pop3"
	- Checksum
	- source address
	- destination address
	- options
	- padding
- **IPv6**
	- version
	- traffic class
		- QoS, DSCP, Type of Service
	- flow label
	- payload length
	- next header
	- hop limit
	- source address
	- destination address
### 2 Data Link Layer - Frame (header and trailer)
**Header**
- preamble
- DST MAC address
- SRC MAC address
- type
- packet
**Trailer**
- FCS (Frame Check Sequence)
- The trailer has a FCS field
	- The receiver, receives the frame and does a **Cyclic Redundancy Check** (CRC or mathematical calculation) on the frame to see if the number it solves for matches the FCS number to make sure no data was loss, damaged, or corrupted
	- if the calculations don't match, we have a CRC error and data is not used
- If there is a CRC error, does it get retransmitted?

- If using TCP then yes
	- will resend back  over necessary data
- if UDP then no
	- Will not resend back over Wi-Fi

- Preamble: tells the client/host  to listen to your computer as your want to establish communication with them
- MAC addressing
- Type depends on the type of ethernet you are using and what is happening at the upper layer headers
- The layer 2 header and trailer are always changing as data goes to new subnets/vlans/broadcast domains
### 1 Physical Bits

Applications are coded by default to use certain application layer protocols for communication.
Port numbers range from 0-65535
Source ports will be randomly chose n from the range of 49152-65535
Ports 0-1023 are well known ports
ports 1024-49151 are registered ports
Should memorize commonly used ports among application layer

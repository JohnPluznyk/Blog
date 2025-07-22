The following blog/article is everything I learned in my CompT Network+ course.  This blog/article is for me to refresh my knowledge on the networking course and a way for me to review everything I learned.  The order of topics in this article will follow the OSI model from bottom to top, networking concepts, networking security, etc... **Need to edit** 
# OSI Model - Networking Models
## 7. Application - Data
	- not the app itself
	- higest layer
	- the backend software/protocol that interacts with the software
## 6. Presentation - Data
	- End-to-end data encryption, compression, and translation services
	- Not really apart of the TCP/IP stack
## 5. Session - Data
	- Session management / formation / teardown
	- it is about establishing, managing, terminating sesions, connections between devices or application
## 4. Transport - Segment
	- PDU = Segment
	- End to End connections / Segment / TCP and UDP
	- Responsible for how we are going to transport this data from host device to client or client to host
	- UDP = Datagram
	- TCP = Segment
## 3. Network - Packet
	- Packets
	- Routers
	- Layer 3 switches
	- Error checking
	- Routing packets
	- uses information at the network layer in order to make forwarding decisons
	- IPv4 / IPv6 and ICMP (Internet Control Message Protocol) Addressing
	- Takes packets that have IP addressing information in them and routers them from one network to another network
## 2. Data Link - Frame
	- Frames
	- Brains of the physical layer
	- framing and frame switching / switching/ Mac addressing / ARP / CRC
	- ** takes the baw bits/data and convers them back into frames and formats them properly **
	- also convers the frames into raw bits/data
	- FRAME = Layer 2
	- Frames are used to communicate with devices within the same Subnet/Vlan/Broadcast Domain
	- MAC addresses allow us to physically identify the Network Interface Card (NIC) of a device
	- Error detection using frame check sequences and (CRC) cynically redundancy checks
	- Different rules
		- CSMACD
		- CSMACS
	- Network interfaces cards reside at Layer 2 and Layer 1
		- physical NIC for the physical layer
		- Internal components of the NIC can do framing and read and understand MAC addresses
	- Layer 2 switches
	- framing
	- Layer 2 switches look at MAC addresses only
	- make forwarding decisons based on MAC addresses
	- forwards data ONLY BETWEEN DEVICES IN THE SAME SUBNET, VLAN, BROADCAST domain
## 1. Physical - bits
	- bits/physical connectivity / hubs
	- responsible for transmitting raw binary data 0's and 1's
	- physical signal transmisson
	- optical signal

`Google - "The OSI Model can be seen as **a universal language for computer networking**. It is based on the concept of splitting up a communication system into seven abstract layers, each one stacked upon the last. Each layer of the OSI Model handles a specific job and communicates with the layers above and below itself."

When an application wants to send data over the internet, it follows the OSI model starting from the top and packages the data into segments, packet, frame, and transports the bits off to its router which should then send the data to correct network.  From there the receiving device takes the bits and reconstructs the PDUs starting from 1 going to 7.

Any time you are sending data from one computer to another you should ask these questions for each layer.

7 Application - What protocol are using to send the data?
6 Presentation - How is the data going to be presented/formatted/encrypted
5 Session - Is there a session/connection established?
4 Transport - How are going to transport the data? UDP/TCP?  Which port? Reference Application layer
3 Network - What network does the host/node live on?
2 Data Link - How are we connected/linked to the network?
1 Physical - Can we physically transport the data? RF? Ethernet methods? light, eltectic?
## TCP and UDP
- TCP and UDP takes place in the Transport layer (layer 4)
- Two most commonly used protocols at the Transport layer for transport of data
### TCP (Transmission Control Protocol)
- reliable communication
- connection type: connection-oriented
- Sequencing: yes
- PDU name: segment
- Uses: File sharing, downloading, (Https, FTP, SMTP, SSH, Telnet) 
	- TCP is used when the data is Important and if their is loss of data which could cause corruption
	- If data is loss, the device will request for that missing data
### UDP (Universal Datagram Protocol)
- Best effort
- Connection type: connectionless
- Sequencing type: No
- PDU name: datagram
- Uses: VoIP, Streaming  video, (DNS, DHCP, VoIP, TFTP, NTP)

- 90% of the traffic within a network will most likely be TCP based.

- What does reliable vs unreliable communication mean?
	- A reliable communication means it has the ability to detect whether or not a communication is being sent and received in the correct matter so that the recipient can read the data correctly.  If there is a mistake in the communication, TCP can fix this mistake by re-requesting for the missing/corrupted data needed in order to interpret the message
	- UDP does not detect whether or not the data being received is correct
- Connection oriented means that the two computers establish a connection/session with each other before data is sent out over the internet
	- Once a connection/session is established with two hosts, computers can now perform **SEQUENCING** which is a part of the TCP segment
- **Sequencing** allows the sender to keep track of every single byte that is sent out to the receiver
	- The receiver then needs to confirm that they received all of the correct data/bytes
	- If it is missing any data, it will request for missing data

- UDP - if you need to send data to a device, you just send it.  If the device is listening, it will receive and interpret the data.  No connection is established/required.
	- UDP better bandwidth, better throughput
	- If something goes wrong with UDP that is up to the human to interpret what is missing

- TCP will cause lag if data need to be retransmitted

## TCP vs UDP
- Transmission Control Protocol
	- TCP reliable
	- TCP connection oriented
	- packet sequencing and reliable delivery
	- flow control and error checking
- User Datagram Protocol
	- UDP connectionless
	- UDP faster, less data transmitted
	- best effort
	- no data recovery

## 3-Way handshake (TCP)
- SYN = Synchronize
- SYN/ACK = Synchronize/Acknowledge
- ACK = Acknowledge

- What are we trying to do with this handshake?
	- We are trying to establish a bi-directional communication

- The first SYN corresponds to the first ACK while the second SYN corresponds to the second ACK

Client SYN --> Client
Client <-- Syn/ACK Client
Client ACK --> Client
## Window Size
- Window size = how many bytes of data we can send before we need an acknowledgement
	- Window size range = [0-65535 bytes]
- How does the windows size work exactly
	- The sender will send the indicated amount of data given in the windows size
	- The receiver will make sure that they have gotten all of the data indicated by the window size
	- If the receiver gets all the data indicated by the window size it will send an ACK back to the sender, letting them know they got all the necessary data
	- **If the sender does not get all the data, it will send out a request to the sender to resend the data it is missing**
- Flow Control / Sliding Window
	- Allows to increase and decrease the window size in order to increase network performance in case of bad connection between two clients
	- You can see a real world example of then when downloading a file and seeing download rate increase and decrease
- TCP 3 way handshake starts every time you request for a new service
## When nobody is listening
- TCP sends a RST (Reset) packet when a SYN is received on a non-listening port
- If RST flag is set, it means no one is listening
	- What does this mean?
	- it means: a computer attempted to make a connection and the receiver is not listening
Client  SYN-->  Client
Client  <-- RST   Client
## Packet MTU
- 1500 bytes
- The packet goes within your ethernet frame
	- The frame is about 18 bytes
	- Creates a total of 1518 bytes or less
	- How the window size is chosen is backed into the TCP protocol itself
## TCP flags
- FIN for finish
	- Once there is no more data to transmit a FIN flag will be sent to notify the receiver that there is no more data and the TCP session can be torn down
	- tear TCP session down
	- If a connection is left open a malicious user could take advantage
	- Most sessions will automatically close in 30 seconds if no data is being transmitted
- 0x002 (SYN)
## ICMP (Internet Control Message Protocol) - Network Layer Protocol - Layer 3 (L3)
- Connectionless protocol
	- Network messaging
		- Destination unreachable
		- redirect
		- Time exceeded - TTL - Time To Live
	- Network Diagnostics
		- Ping
			- Echo request
			- Echo reply
		- Traceroute
- ICMP is its own protocol
	- only relies on layers 3,2,1
	- Does not rely on upper layers of OSI model
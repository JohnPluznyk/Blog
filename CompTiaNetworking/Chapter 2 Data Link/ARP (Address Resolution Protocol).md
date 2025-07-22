**ARP - Layer 2 protocol**
- ARP is for Layer 3  (IP - Internet Protocol) to Layer 2 (MAC) Mapping
	- ARP requests are sent only within a VLAN/Subnet/Broadcast Domain because ARP is a Layer 2 broadcast
	- Local devices store their mappings in a cache
	- Layer 3 capable devices ask who owns certain IP addresses using FF:FF:FF:FF:FF:FF to broadcast their ARP requests
	- Only device with the IP address responds
	- ARP maps IP to MAC

**Encapsulation**
- The source address comes from the device sending the request
	- How do we get the destination address / IP address?
		- **DNS - Domain Name System** UDP/TCP port 53 - resolves website addresses to IP addresses
	- Source MAC is burned into NIC
	- The DST MAC is whoever we send frame to
		- We get DST MAC from ARP
	- So if we have to send frame to another PC within the PCs subnet we  use ARP to get their MAC

**ARP Process**
- **ARP request** - devices sends out a layer 2 broadcast requesting for MAC address of a specific IP address
- **ARP reply** - the owner of the IP address will respond with their own MAC address
- **ARP cache** - the information learned from ARP is placed in a cache

**ARP Cache**
- Routers, L3 switches, IP hosts all have ARP caches
- **Exam Note: L2 switches do not need an ARP cache**
	- L2 switches do not need ARP cache because they never take apart frames
	- L2 switches also **DO NOT BUILD Frames**
	- **L2 switches simply make forwarding decisions based on the MAC address within a frame**
	- The ARP cache keeps a record of recent binding of IP addresses to MAC addresses for later use
		- So a device does not have to keep making ARP request for same IP

**ARP spoofing as On-Path Attacks**
- On-Path Attacks
	- ARP spoofing/ARP poisoning (pretend to be the IP address of the default gateway)
		- Reply to an ARP request with the wrong MAC address (reply with malicious device address)

Layer 2 switches forwards frames using a MAC address table
Layer 2 switches do not have ARP cache

ARP is L2 and L3.  ARP binds an IP address to MAC address
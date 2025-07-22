**Types of addresses**
- MAC (L2) Layer 2 addres
	- ex: ffff ffff ffff
	- ffff = 16-bits in hexadecimal
	- 48 bits in total 4 * 12 = 48
	- 12 hex characters
- IPv4 (L3) Layer 3 address
	- ex: 255.255.255
	- ex: 11111111.11111111.11111111.11111111
	- represented with decimal or binary
	- 32 bits total
- IPv6 (L3) Layer 3 address
	- ffff ffff ffff ffff ffff ffff ffff ffff
	- 128 bits total
**Host OS Commands for L2 addresses - MAC addresses**
- Windows
	- ipconfig /all
- MAC
	- ifconfig
	- ip addr show "name of network interface
- Linux
	- ifconfig
	- ip addr show "name of network interface"

**Types of L2 Communication - only happens within the same subnet/vlan/Broadcast Domain** 
- Unicast (1 to 1)
	- Destination MAC: Specific MAC address
	- Source MAC: Specific MAC address
- Broadcast
	- Destination MAC: FF-FF-FF-FF-FF-FF
	- Source MAC: Specific MAC address
	- Goes to everyone in the same subnet/vlan that you are in
	- we know this broadcast because of the destination MAC being all F's
- Multicast
	- Destination MAC: 01:00:5e:xx:xx:xx
	- Source MAC: specific MAC address
	- Have to subscribe to group

**Host OS Commands for L3 addresses - Network address - IP/IPv4/IPv6**
- Windows
	- ipconfig /all
- MAC
	- ifconfig
	- ip addr show "name of network interface
- Linux
	- ifconfig
	- ip addr show "name of network interface"

**Classes of IPv4 Addresses**

| Address Class | First Octet | Address Type    |
| ------------- | ----------- | --------------- |
| Class A       | 1-126       | Host Addressing |
| Class B       | 128-191     | Host Addressing |
| Class C       | 192-223     | Host Addressing |
| Class D       | 224-239     | IPv4 Multicast  |
| Class E       | 240-255     | Experimental    |
- Class A use case: Deployed with custom subnets such as /24 tailoring the size of the IP space to something manageable
- Class D use case: sent to subscribers: running the same protocol (OSPF, EIGRP, HSRP) Devices of the same type (routers, hosts) subscribed via IGMP
- Class E use case: effectively unused filtered if ever used as a source internet boundary routers

**L3 types of communication**
- Unicast (1 to 1)
	- Destination IP: Specific IP address
	- Source IP: Specific IP address
- Broadcast (1 to everyone)
	- Destination IP: 255.255.255.255
	- Source IP: Specific IP address
- Multicast (1 to group): devices subscribe to communication stream
	- Destination IP: 239.10.157.88
	- Source IP:  specific IP address
	- If class D IP address 224-239

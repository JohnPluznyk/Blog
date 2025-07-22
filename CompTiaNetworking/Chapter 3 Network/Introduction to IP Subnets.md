## Subnets
- A subnet is identified by pairing of an IP address and a subnet mask.
- The subnet mask indicates the bits all hosts in the subnet must share
- Can represent subnet with decimal (255.255.255.0), hexadecimal (0xffff0000), or slash notation (/24)

**IP address structure**
- Hosts in the same LAN must share the same values in the "subnet" portion of the address
	- subnet: 10.49.6.-    Host: .1     IP address = 10.49.6.1
	- subnet: 10.49.6.-    Host: .221   IP address = 10.49.6.221
	- Both addresses have 255.255.255.0 subnet masks or /24 in slash notation
- A subnet is like a street name
- Host is like the house on the street
- Addressing is not secretive

**Subnets and VLANs**
- Each subnet gets its own VLAN in a group of interconnected switches
- VLANS are a way for us to do virtualization of out network environments
	- Smaller more efficient vlan/subnet/broadcast domain
- When you create a VLAN you tag the frame with the specific vlan that the device is connected to
	- When VLANs are used **(802.1Q tagging standard)**, Ethernet frames are tagged with a VLAN ID (added between the source MAC and EtherType fields) 
	- Only tagged when traffic is going through the trunk port
		- Not access ports

**VLAN Segmentation**
- Allows us to have many different users with different roles and responsibilities connected all to one switch
- To segment and isolate certain users traffic to specific VLANs
- users connected to the same VLAN will be able to exchange data
- Allows us to prevent devices not connected to the same vlan/subnet/broadcast domain from sending unnecessary layer 2 (Frames) to devices
- Allows us to provide a layer of security while maximizing port utilization

**VLAN Double Tagging??? Security risk???**
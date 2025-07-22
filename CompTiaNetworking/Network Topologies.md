## Physical Network Topologies
- logical topology
	- how traffic flow
- physical topology
	- how it is cabled / physically laid out

![[Pasted image 20250621153943.png]]
## Bus
- single backbone terminated on each end
- all devices "tap" into one cable
## Ring
- devices are connected in a closed loop
- data travels in one direction
- only one device can communicate
- Need token to have permission
## Star (Hub and Spoke)
- Most common deployment today
- Nodes are connected to a central hub (switch)
- switch acts as a repeater (boost the signal)
- multiple devices can communicate at a time (Full Duplex)
- all spoke traffic will be sent to hub
## Mesh
- all devices connected to each other
- great for the core of your enterprise network
- great for WANs where you need high availability
## Point to Point
- Point to point connections have only two hosts (one for each side of the connection)
- **Exam Note: will commonly have a subenet mask of 255.255.255.252 (/30)**
	- Can only have two devices
- Generic Routing Encapsulation (GRE)
	- Creating a virtual connection across the internet
**Most commonly used today are mesh and star (hub and spoke)**
## LAN Three-tier Hierarchical Model
- Core
	- Mesh
	- backbone
	- Redundancy
	- performance
- Distribution
	- Mesh
	- aggregates everything from Access layer
	- Where you apply policies
- Access
	- uses star
	- Connect users to network

## Models used in everyday environments
- Three-tier hierarchical model
- Two tier or collapsed core
	- scalability becomes an issue
![[Pasted image 20250621154720.png]]

## Spine Leaf - Software Defined Datacenter Networking
- Core/Backbone = core
- Spine = Distrbution
- Leaf = Access

## Network Traffic Flow Terms
- North
	- Traffic going out of network
- South
	- Traffic going into the network
- East West
	- Traffic flowing from one device to another within the same network
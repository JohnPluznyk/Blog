### Frame Switching - Broadcast Flooding
- Switches do one of two different things with frames: **Flooding** or **Forwarding**
	- **Flood:** Frames will be sent (Flooded) out all ports except the ingress port, uses destination MAC address of (FFFF:FFFF:FFFF)
		- Used for ARP

### Frame Switching - Unicast
- **Forward:** Forward Frames out a single port based on the destination MAC address
	- Uses a specific MAC address that lives within the MAC address table of the switch
		- 1:1
	- **Unknown unicast frame**: looks like regular known unicast frame, but the destination MAC address is unknown.
		- so.. the switch flood the frame and not drop it because it is not known

### L2 Multicast Flooding
- **Multicast:** Multicast frames are flooded out all ports except ingress (may be controlled  with IGMP snooping: Beyond the scope of this course)
	- Multicast frames start with the following MAC values: 01:00:5e:xx:xx:xx 

### Layer 2 loops
- We want redundancy in our environment.  Which is just multiple paths a frame can take in case one of the paths go down
- However, if you have two layer 2 switches with multiple connection to each other, it can cause a layer 2 loop when frames are broadcast.  This is because the frame will use the redundant connection and not know what they are doing
#### Uncontrolled Layer 2 loops will cause:
- Broadcast storms
- Mac table instability
- extreme latency
- effectively makes an entire vlan unusable
- Time To Live counter does not decrement because it only decrements when it goes from router to router
## How can we stop Layer 2 Loops but keep redundancy?
## Spanning Tree Protocol (STP)
- Identifies ports to block so that loops will be eliminated
- STP analyzes the Layer 2 environment and identifies ports to block so that loops will be eliminated
- STP Communicates via BPDUs (Bridge Protocol Data Units)
	- This is the message exchanged in between the switches in order to identify which ports should be blocked and which should remain open
	- Every 2 seconds a BPDU is exchanged between switches

### Spanning Tree Protocol (STP) Algorithm
**What is the default value of STP**
32768
#### 1) Determine Root Bridge
- Root of the Spanning Tree
- Lowest Bridge (BID) used to elect Root Bridge
- BID = Priority + MAC address
#### 2) Determine Root Ports
- Port on switch with lowest total cost path to the root bridge
	- certain interfaces have specific costs
	- add up cost all of interfaces a frame would take to get to root bridge
	- lowest cost wins
- What if cost is tied?
	- **Analyze BID**
		- If its the same device it will have the same BID
	- What if BID is tied?
		- **Analyze Port ID**
		- smaller port ID wins
- One Root port per switch
#### 3) Determine Designated Ports (DP)
- Port on link with lowest total cost path to the root bridge
- every port on the root bridge is a DP
- What if tie?
	- Determine costs of ports needed to take to get to Root bridge
- What if costs is tied?
	- Use BID
		- BID = Priority + MAC Address
		- small BID wins
#### 4) Block all other ports

### Common causes of Layer 2 loops
- devices are not able to run STP are at a L2 risk
	- unmanaged switches
	- Hubs
- Note: Redundant cabling from any non-STP enabled device will cause a L2 loop

### STP Operation and LED troubleshooting
- If a port is in the blocking state it will be "Amber STP Block"
	- Not true for all switches *cisco*


| Port Role            | Port State |
| -------------------- | ---------- |
| Root Port (RP)       | Forwarding |
| Designated Port (DP) | Forwarding |
| Non-designated Port  | Blocking   |

### IEEE 802.1D
- The standard implementation of STP aka: classic STP.
- Slow to adapt to topology changes (30 to 50 seconds)
### IEEE 802.1W
- Rapid Spanning tree protocol
- fast to adapt to topology changes (2 seconds or less)
### IEEE 802.1S
- use when using cisco and non-cisco devices
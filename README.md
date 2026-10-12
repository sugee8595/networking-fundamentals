# Networking Fundamentals

Self-directed deep dive into core networking concepts, built through Cisco's Networking Academy (Networking Basics, certified) plus independent practice and research.

## Topics Covered

### OSI Model vs TCP/IP Model
- OSI: 7-layer theoretical reference model (Physical, Data Link, Network, Transport, Session, Presentation, Application)
- TCP/IP: 4-layer practical model the internet actually runs on (Network Access, Internet, Transport, Application)
- TCP/IP merges OSI's Session, Presentation, and Application layers into one Application layer

### Encapsulation Flow (Data journey, sender to receiver)
1. **Application layer** — raw data (e.g., HTTP request)
2. **Transport layer** — becomes a **segment** (TCP adds port numbers, ensures reliable delivery; UDP is faster but unreliable)
3. **Network layer** — becomes a **packet** (IP adds source/destination IP addresses, enables routing)
4. **Data Link layer** — becomes a **frame** (MAC addresses added, delivery within one local link)
5. **Physical layer** — becomes **bits** (electrical signal, light pulses, or radio waves depending on medium)

De-encapsulation happens in reverse on the receiving end.

### Key Insight: MAC vs IP
- **IP address** stays the same for the entire end-to-end journey (except one NAT translation)
- **MAC address** changes at every router hop — it only has meaning within one local network (LAN)
- A router strips and rebuilds the Layer 2 frame at every hop, while the Layer 3 packet's IP addresses remain constant

### Subnetting
- A subnet mask defines which bits of an IP address are "network" vs "host" (e.g., 255.255.255.0 = /24)
- CIDR notation (/24, /16, etc.) counts the number of "1" bits in the mask
- Example: /24 = 254 usable host addresses (256 total, minus network address and broadcast address)

### NAT (Network Address Translation)
- Translates private IPs (192.168.x.x, 10.x.x.x, 172.16-31.x.x) into a single shared public IP for internet access
- Router maintains a translation table to route return traffic to the correct internal device
- Creates challenges for peer-to-peer connections (NAT traversal problem) since NAT is designed for outbound-initiated connections

### ARP (Address Resolution Protocol)
- Resolves an IP address to its corresponding MAC address within a LAN
- Used whenever a device needs to deliver a frame but only knows the destination's IP

### DHCP (Dynamic Host Configuration Protocol)
- Automatically assigns IP addresses to devices joining a network (DORA process: Discover, Offer, Request, Acknowledge)
- Eliminates manual IP configuration and reduces human error compared to static addressing

### DNS (Domain Name System)
- Translates human-readable domain names into IP addresses
- Resolution chain: local cache → DNS resolver → root server → TLD server → authoritative server

### Firewalls
- Packet-filtering, stateful inspection, proxy (application-layer), and next-generation firewalls (NGFW)
- Control inbound/outbound traffic based on defined rules

### Broadcast Domains
- A broadcast packet has all 1s in the host portion of its destination IP
- Routers block broadcasts by default, acting as the boundary of a broadcast domain

## Tools Practiced
- `ping`, `tracert`/`traceroute`, `ipconfig`, `nslookup`, `arp -a`
- Wireshark (packet capture and protocol filtering — in progress)

## Certification
Cisco Networking Academy — Networking Basics (Completed, October 2026)

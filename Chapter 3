# Chapter 3 — Networking Terminology
### (Cybersecurity / Ethical Hacking Perspective)

This chapter builds the vocabulary you'll need to read CVEs, pentest reports, packet captures, and threat intel — the "language" of both networking and hacking.

---

## 1. Core Addressing Terms

| Term | Meaning | Security Relevance |
|---|---|---|
| **IP Address** | Logical address identifying a device on a network (IPv4/IPv6) | Basis of scanning, targeting, geolocation, IP spoofing |
| **MAC Address** | Physical/hardware address of NIC (48-bit) | Used in ARP spoofing, MAC filtering bypass |
| **Subnet Mask** | Defines network vs host portion of an IP | Used to define pentest scope, VLAN segmentation |
| **Default Gateway** | Device that routes traffic outside the local network (usually router) | Common MITM target (ARP spoofing to impersonate gateway) |
| **DNS (Domain Name System)** | Translates domain names to IP addresses | Target of DNS spoofing/poisoning, DNS tunneling (data exfil) |
| **DHCP** | Automatically assigns IP addresses to devices | Rogue DHCP server attacks, DHCP starvation |

---

## 2. Connection & Session Terms

| Term | Meaning | Security Relevance |
|---|---|---|
| **Port** | Logical endpoint for communication (0–65535) | Port scanning identifies attack surface |
| **Socket** | Combination of IP + Port | Identifies a specific communication channel to exploit/monitor |
| **Session** | A continuous connection between two devices | Target of session hijacking |
| **Handshake** | Initial exchange to establish connection (e.g., TCP 3-way handshake) | Abused in SYN flood DoS attacks |
| **Bandwidth** | Max data transfer capacity | Target of DDoS/bandwidth exhaustion attacks |
| **Latency** | Delay in data transmission | Can indicate MITM or tunneling overhead |

---

## 3. Traffic & Data Terms

| Term | Meaning | Security Relevance |
|---|---|---|
| **Packet** | Small unit of data transmitted over a network | Sniffed/analyzed via Wireshark; basis of all traffic analysis |
| **Frame** | Data unit at Data Link layer (contains MAC info) | Analyzed in Layer 2 attacks (ARP spoofing, VLAN hopping) |
| **Protocol** | Set of rules governing communication | Weak protocols (Telnet, FTP) are common exploit targets |
| **Encapsulation** | Wrapping data with headers as it moves down OSI layers | Understanding this is key to reading packet captures |
| **Broadcast** | Message sent to all devices on a network | Abused in broadcast storm/amplification attacks |
| **Unicast/Multicast** | One-to-one / one-to-many communication | Relevant to traffic analysis and network mapping |

---

## 4. Network Boundary & Control Terms

| Term | Meaning | Security Relevance |
|---|---|---|
| **Firewall** | Filters traffic based on rules | First line of defense; also first thing attackers try to evade |
| **Router** | Directs traffic between networks | Misconfigurations lead to exposure of internal networks |
| **Switch** | Connects devices within a LAN | Target of MAC flooding, VLAN hopping |
| **Proxy** | Intermediary between client and server | Used both defensively (filtering) and offensively (anonymizing attacker traffic) |
| **VPN** | Encrypted tunnel over a public network | Target of credential attacks; also a defensive tool |
| **NAT (Network Address Translation)** | Maps private IPs to a public IP | Complicates traceability; relevant to IP spoofing/scanning limitations |

---

## 5. Common Acronyms Cheat Sheet

| Acronym | Full Form |
|---|---|
| LAN/WAN/MAN | Local/Wide/Metropolitan Area Network |
| ISP | Internet Service Provider |
| TCP/UDP | Transmission Control Protocol / User Datagram Protocol |
| ARP | Address Resolution Protocol |
| DNS | Domain Name System |
| DHCP | Dynamic Host Configuration Protocol |
| NAT | Network Address Translation |
| VPN | Virtual Private Network |
| SSID | Service Set Identifier (WiFi network name) |
| MTU | Maximum Transmission Unit |

---

## 6. Why Terminology Matters for a Hacker/Analyst

- **Reading a CVE or threat report** requires fluent understanding of these terms (e.g., "attacker performed ARP spoofing to intercept the TCP session before the DHCP lease expired").
- **Writing a pentest report** requires precise terminology so findings are unambiguous and actionable.
- **Using tools** (Nmap, Wireshark, Burp Suite) constantly surfaces this vocabulary in their output — without it, tool output is unreadable.

---

## Quick Revision Points
- IP = logical address, MAC = physical address — both are spoofable and both are attacked differently.
- Ports/sockets define *where* an attack surface exists on a device.
- Packets and frames are what you actually inspect during traffic analysis.
- Firewalls, routers, switches, proxies, VPNs, NAT are the core control points attackers try to bypass or abuse.
- Fluency in this vocabulary is a prerequisite to understanding any CVE, tool output, or pentest report.


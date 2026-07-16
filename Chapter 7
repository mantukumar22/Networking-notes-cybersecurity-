# Chapter 7 — TCP/IP Model
### (Cybersecurity / Ethical Hacking Perspective)

While the OSI model is the theoretical reference, **TCP/IP is the model actually implemented in real-world networks and the Internet.** Every tool you use (Nmap, Wireshark, Metasploit) works against TCP/IP in practice.

---

## 1. What Is the TCP/IP Model?

A 4-layer (sometimes described as 5-layer) practical model that maps directly onto how the Internet actually functions. It condenses the OSI model's 7 layers into 4 functional layers.

---

## 2. The 4 Layers of TCP/IP

| TCP/IP Layer | Equivalent OSI Layers | Function |
|---|---|---|
| **Application** | Application, Presentation, Session (L5–L7) | User-facing protocols: HTTP, FTP, DNS, SMTP, SSH, Telnet |
| **Transport** | Transport (L4) | End-to-end delivery: TCP (reliable), UDP (fast/unreliable) |
| **Internet** | Network (L3) | Logical addressing & routing: IP, ICMP, ARP |
| **Network Access (Link)** | Data Link, Physical (L1–L2) | Physical transmission, MAC addressing, framing |

---

## 3. TCP vs UDP (Critical for Security Work)

| Feature | TCP | UDP |
|---|---|---|
| Connection | Connection-oriented (3-way handshake) | Connectionless |
| Reliability | Reliable (acknowledgments, retransmission) | Unreliable (no guarantee) |
| Speed | Slower (overhead) | Faster |
| Use Cases | HTTP, HTTPS, FTP, SSH, Email | DNS, VoIP, streaming, DHCP |
| **Security Relevance** | Target of SYN floods, session hijacking, sequence prediction | Target of UDP floods, amplification attacks (DNS, NTP amplification) |

> **Why it matters:** Nmap's TCP scans (SYN scan, Connect scan) vs UDP scans behave completely differently — UDP scanning is slower and less reliable precisely because of this connectionless nature, which is also why UDP-based amplification DDoS attacks are so effective (no handshake verification needed).

---

## 4. The TCP 3-Way Handshake (Must-Know for Security)

1. **SYN** — Client sends synchronize request to server
2. **SYN-ACK** — Server acknowledges and sends its own sync request
3. **ACK** — Client acknowledges — connection established

**Security relevance:**
- **SYN Flood Attack:** Attacker sends many SYN packets but never completes the handshake (no final ACK), exhausting server resources holding half-open connections.
- **Nmap SYN Scan ("stealth scan"):** Sends SYN, receives SYN-ACK, but never sends the final ACK — used to detect open ports without completing a full connection (harder to log).

---

## 5. IP Layer Essentials (Internet Layer)

- **IP (Internet Protocol):** Provides logical addressing and routing — IPv4 (32-bit) and IPv6 (128-bit).
- **ICMP (Internet Control Message Protocol):** Used for diagnostics (ping, traceroute) — also abused in ICMP flood/Smurf/Ping of Death attacks.
- **ARP (Address Resolution Protocol):** Resolves IP to MAC address on a local network — the protocol behind ARP spoofing/poisoning attacks.

---

## 6. OSI vs TCP/IP — Side-by-Side Comparison

| Aspect | OSI Model | TCP/IP Model |
|---|---|---|
| Layers | 7 | 4 |
| Nature | Theoretical/reference | Practical/implemented |
| Usage | Used for teaching, categorizing attacks/tools | Used in actual Internet architecture |
| Developed by | ISO | DoD (US Department of Defense) |

> **Security takeaway:** You'll use OSI language to *describe and categorize* an attack ("this is a Layer 4 attack"), but the actual packets you capture and analyze in Wireshark are structured according to **TCP/IP** in practice.

---

## 7. Why TCP/IP Matters for Ethical Hacking

- **Every scanning tool** (Nmap, Masscan) is fundamentally a TCP/IP manipulation tool — crafting and interpreting SYN, ACK, RST, FIN flags.
- **Firewalls and IDS/IPS rules** are written in terms of TCP/IP (source/destination IP, port, protocol, flags).
- **Most real-world attacks reference TCP/IP behavior directly:** SYN flood, TCP RST injection (used in some censorship/MITM tools), IP fragmentation attacks (used to evade IDS).

---

## Quick Revision Points
- TCP/IP has 4 layers: Application, Transport, Internet, Network Access — maps onto OSI's 7.
- TCP = reliable, handshake-based (SYN floods, sequence attacks); UDP = fast, connectionless (amplification attacks).
- The 3-way handshake (SYN, SYN-ACK, ACK) is the basis of both legitimate connections and major DoS techniques.
- ARP, ICMP, IP are the core Internet-layer protocols — and each has a signature attack (ARP spoofing, ICMP flood, IP spoofing).
- OSI = theory/classification language; TCP/IP = what's actually running on real networks and what your tools manipulate.


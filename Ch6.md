# Chapter 6 — OSI Model
### (Cybersecurity / Ethical Hacking Perspective)

> **This is the single most important theoretical chapter for a cybersecurity/ethical hacking career.** Nearly every attack, tool, and defense mechanism is described in terms of "which OSI layer" it operates at. If you master this chapter, everything else (protocols, attacks, tools) becomes far easier to categorize and understand.

---

## 1. What Is the OSI Model?

**OSI = Open Systems Interconnection** — a 7-layer conceptual model that standardizes how data moves from one device to another across a network. Each layer has a specific job and hands data to the layer below/above it.

**Mnemonic (top to bottom):** "**A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing"
(Application, Presentation, Session, Transport, Network, Data Link, Physical)

---

## 2. The 7 Layers — Function + Attacks at Each Layer

### Layer 7 — Application
- **Function:** Interface between user applications and the network (HTTP, FTP, DNS, SMTP, etc.)
- **Attacks here:**
  - SQL Injection, XSS, Cross-Site Request Forgery (CSRF)
  - Phishing, malware delivery
  - Application-layer DDoS (e.g., HTTP flood)
- **Tools:** Burp Suite, OWASP ZAP

### Layer 6 — Presentation
- **Function:** Data translation, encryption/decryption, compression (SSL/TLS operates conceptually here)
- **Attacks here:**
  - SSL/TLS downgrade attacks, weak cipher exploitation
  - Malformed data/encoding attacks (Unicode exploits)

### Layer 5 — Session
- **Function:** Establishes, manages, and terminates sessions between applications
- **Attacks here:**
  - Session hijacking
  - Session fixation

### Layer 4 — Transport
- **Function:** End-to-end communication, reliability (TCP), speed (UDP), segmentation, flow control
- **Attacks here:**
  - SYN Flood (abusing TCP 3-way handshake)
  - Port scanning (Nmap operates heavily here)
  - UDP flood attacks

### Layer 3 — Network
- **Function:** Logical addressing (IP) and routing between networks
- **Attacks here:**
  - IP Spoofing
  - ICMP flood (Ping of Death, Smurf attack)
  - Routing attacks (BGP hijacking)

### Layer 2 — Data Link
- **Function:** Physical addressing (MAC), framing, error detection within a local network (switches operate here)
- **Attacks here:**
  - ARP Spoofing/Poisoning
  - MAC Flooding
  - VLAN Hopping

### Layer 1 — Physical
- **Function:** Actual transmission of raw bits over physical medium (cables, radio waves, hubs, NICs)
- **Attacks here:**
  - Wiretapping
  - Cutting cables (physical DoS)
  - Jamming (wireless signal interference)

---

## 3. OSI Layer Attack Reference Table

| Layer | Name | Key Protocols/Devices | Common Attacks |
|---|---|---|---|
| 7 | Application | HTTP, FTP, DNS, SMTP | SQLi, XSS, phishing, app-layer DDoS |
| 6 | Presentation | SSL/TLS, encoding | SSL downgrade, encoding exploits |
| 5 | Session | NetBIOS, RPC, sessions | Session hijacking, fixation |
| 4 | Transport | TCP, UDP | SYN flood, port scanning |
| 3 | Network | IP, ICMP, Routers | IP spoofing, ICMP flood, BGP hijack |
| 2 | Data Link | MAC, Switches, ARP | ARP spoofing, MAC flooding, VLAN hopping |
| 1 | Physical | Cables, Hubs, NICs, Radio | Wiretapping, jamming, cable cutting |

---

## 4. Encapsulation & De-encapsulation

- **Encapsulation:** As data moves DOWN the layers (sender side), each layer adds its own header (and sometimes trailer) — this is how a "Packet" becomes a "Frame" becomes "Bits."
- **De-encapsulation:** As data moves UP the layers (receiver side), each layer strips its corresponding header.

**Data unit names per layer (important for packet analysis):**
| Layer | Data Unit Name (PDU) |
|---|---|
| Transport | Segment (TCP) / Datagram (UDP) |
| Network | Packet |
| Data Link | Frame |
| Physical | Bits |

> **Why this matters:** When you open Wireshark, you're literally looking at encapsulated data — Ethernet frame (L2) containing an IP packet (L3) containing a TCP segment (L4) containing HTTP data (L7). Understanding this stack is essential to reading any packet capture.

---

## 5. Why the OSI Model Is Central to Ethical Hacking

1. **Categorizing attacks:** Every attack can be labeled by OSI layer — this is literally how CEH, Security+, and pentest reports classify findings.
2. **Choosing the right tool:** Nmap operates mostly at L3/L4, Wireshark spans all layers, Burp Suite is L7-focused, aircrack-ng works at L1/L2 for wireless.
3. **Defense-in-depth thinking:** Good security is layered — firewall (L3/L4), IDS/IPS (multiple layers), WAF (L7), encryption (L6) — the OSI model IS the blueprint for layered defense.
4. **Troubleshooting mindset:** "Is this a Layer 1 problem (cable unplugged) or a Layer 7 problem (app misconfigured)?" — same diagnostic mindset applies to figuring out *where* an attack is happening.

---

## Quick Revision Points
- 7 layers, top to bottom: Application, Presentation, Session, Transport, Network, Data Link, Physical (mnemonic: All People Seem To Need Data Processing).
- Each layer has its own set of associated attacks — memorize the attack-to-layer mapping, it's exam and real-world gold.
- PDU names: Segment (L4) → Packet (L3) → Frame (L2) → Bits (L1).
- Encapsulation/de-encapsulation is exactly what you see when analyzing packets in Wireshark.
- The OSI model is the universal language for categorizing both attacks and defenses.


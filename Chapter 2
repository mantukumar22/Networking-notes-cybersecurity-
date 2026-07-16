# Chapter 2 — Introduction to Computer Network
### (Cybersecurity / Ethical Hacking Perspective)

## 1. What Is a Computer Network?

A computer network is a collection of two or more devices (nodes) connected together to **share resources, data, and communication paths**. From a security standpoint, a network is simply a set of **trust boundaries and data paths** — and every boundary and path is a potential attack surface.

> **Security lens:** A network doesn't just connect devices — it connects *risk*. Every device added to a network extends the attack surface of every other device on it.

---

## 2. Basic Components of a Network

| Component | Function | Security Relevance |
|---|---|---|
| Node (Host) | Any device (PC, server, phone, IoT) | Each node = potential entry/pivot point |
| Server | Provides services/resources | High-value target (data, credentials) |
| Client | Requests services | Common initial compromise point (phishing, malware) |
| Transmission Medium | Cable/wireless carrying data | Interception point (sniffing, tapping) |
| NIC (Network Interface Card) | Connects device to network, has MAC address | MAC spoofing possible |
| Protocol | Rules for communication | Exploited if implemented insecurely |

---

## 3. Why Networks Exist (Purpose)

- Resource sharing (printers, files, storage)
- Communication (email, chat, VoIP)
- Centralized data management (databases, servers)
- Remote access (VPN, RDP, SSH)

**Security implication:** Every one of these legitimate purposes is also an **abuse case**:
- File sharing → lateral movement of malware/ransomware
- Communication → phishing, social engineering delivery
- Centralized data → single point of high-value compromise (databases are prime ransomware/exfiltration targets)
- Remote access → #1 abused entry point (RDP brute-force, VPN exploits are consistently top initial-access vectors in breach reports)

---

## 4. Types of Networks (by Size/Scope)

| Type | Range | Example | Security Note |
|---|---|---|---|
| PAN (Personal Area Network) | A few meters | Bluetooth, USB | Bluetooth sniffing/jamming attacks |
| LAN (Local Area Network) | Building/campus | Office network | Most pentests start here (internal network testing) |
| MAN (Metropolitan Area Network) | City-wide | Cable TV networks, city ISPs | Less common attack focus but relevant to ISP-level attacks |
| WAN (Wide Area Network) | Country/global | The Internet | Where external/remote attacks originate |

**Why this matters for pentesting:** Scope of an engagement is usually defined by network type — "internal pentest" = LAN, "external pentest" = WAN-facing assets.

---

## 5. Network Architecture Models

### a) Peer-to-Peer (P2P)
- No central server; each device shares/accesses resources equally.
- **Security risk:** No centralized access control or logging — harder to audit, easier to spread malware peer-to-peer (e.g., old worm propagation, some ransomware).

### b) Client-Server
- Central server manages resources; clients request access.
- **Security advantage:** Centralized authentication, logging, and access control (easier to secure and monitor).
- **Security risk:** Server becomes single point of failure/attack — if compromised, entire network is compromised (hence why servers are hardened, patched, and monitored first).

---

## 6. Data Communication Basics

Every communication involves:
1. **Sender** — originates data
2. **Receiver** — destination of data
3. **Message** — the actual data
4. **Medium** — path data travels (wired/wireless)
5. **Protocol** — agreed rules for communication

> **Security angle:** Attackers manipulate one or more of these five elements:
> - Spoof the **sender** (IP/MAC spoofing, email spoofing)
> - Impersonate the **receiver** (rogue DNS, evil twin AP)
> - Alter the **message** (MITM tampering)
> - Tap the **medium** (wiretapping, sniffing)
> - Abuse the **protocol** (exploiting weak/legacy protocols like Telnet, FTP)

---

## 7. Key Takeaway for a Cybersecurity Learner

> "A network is a map of trust. Understanding what a network is, and why it's built the way it is, tells you where trust is assumed — and trust is exactly what attackers exploit."

**Action point:** For every network you encounter (client-server, P2P, LAN, WAN), ask: *"Where is the single point of failure, and where is data most exposed while in transit?"*

---

## Quick Revision Points
- A network = devices + medium + protocols working together.
- Client-Server is easier to secure than P2P (centralized control/logging).
- Network types (PAN/LAN/MAN/WAN) define pentest scope.
- The 5 elements of communication (sender, receiver, message, medium, protocol) are the 5 places attacks happen.
- Remote access and centralized servers are consistently top real-world attack targets.


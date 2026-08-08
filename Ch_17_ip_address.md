# Chapter 17 — IP Address
### (Cybersecurity / Ethical Hacking Perspective)

IP addressing is one of the most practically important topics for a pentester — nearly every recon, scanning, and scoping activity starts with understanding IP addresses and subnets.

---

## 1. What Is an IP Address?

A logical numerical label assigned to a device on a network, used for identification and routing (Layer 3). Comes in two versions: **IPv4** and **IPv6**.

---

## 2. IPv4 Basics

- **Format:** 32-bit address, written as 4 octets (e.g., `192.168.1.1`), each octet 0–255.
- **Total addresses:** ~4.3 billion (now largely exhausted, hence NAT and IPv6).

### IPv4 Address Classes (Legacy but still referenced)

| Class | Range | Default Use |
|---|---|---|
| A | 1.0.0.0 – 126.255.255.255 | Large networks |
| B | 128.0.0.0 – 191.255.255.255 | Medium networks |
| C | 192.0.0.0 – 223.255.255.255 | Small networks (most common in home/office LANs) |
| D | 224.0.0.0 – 239.255.255.255 | Multicast |
| E | 240.0.0.0 – 255.255.255.255 | Reserved/experimental |

---

## 3. Private vs Public IP Ranges

| Type | Range | Security Relevance |
|---|---|---|
| **Private** | 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16 | Not routable on the Internet; used internally; hidden behind NAT |
| **Public** | Everything else (assigned by IANA/ISPs) | Directly reachable from the Internet — primary external attack surface |
| **Loopback** | 127.0.0.0/8 (typically 127.0.0.1) | Refers to the local device itself — used in testing/local services |
| **APIPA** | 169.254.0.0/16 | Auto-assigned when DHCP fails — a sign of misconfiguration, useful troubleshooting indicator |

---

## 4. Subnetting & CIDR Notation

- **CIDR (Classless Inter-Domain Routing):** Notation like `192.168.1.0/24` — the `/24` indicates how many bits are the network portion (24 bits = 255.255.255.0 subnet mask).
- **Why it matters for security:**
  - Defines the **scope of a pentest** — "test 10.0.0.0/24" means testing 256 possible addresses.
  - Understanding subnetting lets you correctly interpret Nmap scan ranges (`nmap 192.168.1.0/24`).
  - Misconfigured subnet boundaries can accidentally expose more of a network than intended (overly broad subnets = larger blast radius if compromised).

### Quick CIDR Reference

| CIDR | Subnet Mask | Usable Hosts |
|---|---|---|
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /30 | 255.255.255.252 | 2 (common for point-to-point links) |

---

## 5. IPv6 Basics

- **Format:** 128-bit address, written in hexadecimal groups (e.g., `2001:0db8:85a3::8a2e:0370:7334`).
- **Why it exists:** IPv4 address exhaustion; provides vastly more address space (no NAT strictly required).
- **Security relevance:**
  - Many organizations run IPv6 **unknowingly or unmonitored** alongside IPv4 — a classic "dual-stack" security gap where IPv6 traffic bypasses IPv4-focused firewall rules (a well-known pentest finding).
  - IPv6's larger address space makes traditional IP-range scanning (brute-force enumeration) impractical — attackers rely more on DNS, multicast, and neighbor discovery for IPv6 recon.
  - **NDP (Neighbor Discovery Protocol)** in IPv6 is the rough equivalent of ARP in IPv4 — and has its own spoofing risks.

---

## 6. IP Spoofing

- **What it is:** Forging the source IP address in packets to disguise the sender's identity or impersonate a trusted host.
- **Used in:**
  - DDoS attacks (hiding attack origin, or reflecting traffic off third parties — e.g., DNS/NTP amplification)
  - Bypassing simple IP-based access control lists
- **Limitation:** Because responses go to the spoofed (fake) address, spoofing is typically only useful for one-way attacks (like flooding), not for establishing a full two-way TCP session (unless combined with other techniques like blind spoofing/sequence prediction).

---

## 7. Why This Matters for Ethical Hacking

- **Scoping a penetration test** almost always starts with a CIDR range — you must be fluent in subnetting to correctly interpret and respect scope boundaries (testing outside the agreed IP range is both unethical and potentially illegal).
- **Network mapping tools** (Nmap, Netdiscover, Angry IP Scanner) output results in terms of IP ranges/subnets.
- **IPv6 is a commonly overlooked security gap** — many security assessments specifically check whether IPv6 firewall rules match IPv4 rules.
- **Understanding private vs public IPs** is essential to distinguishing "internal network testing" from "external/Internet-facing testing."

---

## Quick Revision Points
- IPv4 = 32-bit, written in dotted decimal; IPv6 = 128-bit, written in hex — IPv6 exists due to IPv4 exhaustion.
- Private IP ranges (10.x, 172.16-31.x, 192.168.x) aren't Internet-routable; public IPs are the direct external attack surface.
- CIDR notation (/24, /30, etc.) defines subnet size and directly defines pentest scope boundaries.
- IPv6 is often unmonitored/misconfigured alongside IPv4 — a common real-world security gap.
- IP spoofing forges the source address — powerful for one-way attacks (DDoS) but limited for full two-way sessions without additional tricks.


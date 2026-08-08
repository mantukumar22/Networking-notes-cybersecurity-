# Chapter 16 — How to Setup Local Area Network (LAN)
### (Cybersecurity / Ethical Hacking Perspective)

Setting up a LAN is a practical skill — but every configuration decision made here is also a **security decision**. This chapter connects directly to building a safe home lab for practicing ethical hacking.

---

## 1. Basic LAN Setup Steps

1. **Choose topology** (usually Star — see Chapter 5) with a central switch/router.
2. **Connect devices** via Ethernet cable (Chapter 9) or WiFi (Chapter 13) to the switch/AP.
3. **Configure IP addressing** — either static IPs or DHCP (automatic).
4. **Set up the default gateway/router** for Internet access and inter-network routing.
5. **Configure DNS** (often automatic via ISP or manually set, e.g., to 1.1.1.1 or 8.8.8.8).
6. **Test connectivity** (ping, traceroute) between devices and to the Internet.

---

## 2. Security Considerations During LAN Setup

### a) Network Segmentation from the Start
- Separate networks by purpose using **VLANs**: e.g., a "Guest WiFi" VLAN isolated from the "Corporate/Internal" VLAN.
- **Why:** Prevents a compromised guest device from directly reaching sensitive internal systems — a core defense-in-depth principle.

### b) Router/Switch Hardening
- Change **default admin credentials** immediately (one of the single most common real-world vulnerabilities in SOHO and even some enterprise environments).
- Disable unnecessary services (UPnP, remote management from WAN side, unused ports).
- Keep firmware updated.

### c) DHCP Configuration
- Limit the DHCP address pool to only what's needed (reduces the ability of rogue devices to blend in unnoticed).
- Consider DHCP snooping (on managed switches) to prevent rogue DHCP server attacks.

### d) Static vs Dynamic IP Assignment
| Method | Use Case | Security Note |
|---|---|---|
| **DHCP (Dynamic)** | Most end-user devices | Convenient but makes device tracking/inventory slightly harder without good logging |
| **Static IP** | Servers, network devices, printers | Predictable — good for asset management and firewall rule precision, but must be carefully documented to avoid IP conflicts |

### e) Firewall Rules from Day One
- Configure the router/firewall to **deny by default, allow by exception** — rather than allowing all traffic and trying to block bad things after the fact.

---

## 3. Building a Home Lab for Ethical Hacking Practice

A properly set-up LAN is the foundation of a safe practice environment:

1. **Isolate the lab network** from your main home/production network (separate VLAN or physical switch).
2. **Use virtualization** (VirtualBox/VMware) to run vulnerable VMs (e.g., Metasploitable, DVWA, HackTheBox-style targets) and attacker VMs (Kali Linux) on an internal-only virtual network.
3. **Never expose lab targets directly to the Internet** — vulnerable-by-design machines are dangerous if accidentally reachable externally.
4. **Use a dedicated hypervisor "host-only" or "internal" network mode** so lab traffic never touches your real LAN.

> **Why this matters:** Practicing on a poorly isolated lab network risks accidentally exposing intentionally vulnerable machines to the real Internet — a well-known rookie mistake that has led to real compromises of "practice" environments.

---

## 4. Basic Troubleshooting Commands (Useful in Both Setup and Security Work)

| Command | Purpose |
|---|---|
| `ipconfig` / `ifconfig` | View IP configuration |
| `ping` | Test basic connectivity |
| `tracert` / `traceroute` | Trace the path packets take |
| `arp -a` | View ARP table (useful for spotting ARP spoofing) |
| `netstat -an` | View active connections/listening ports |
| `nslookup` / `dig` | Query DNS records |

---

## 5. Why This Matters for Ethical Hacking

- **Understanding "correct" LAN setup** is what lets you spot **misconfigurations** during a pentest (flat networks, no segmentation, default credentials still in place).
- **Home lab setup skills** are essential for any hands-on ethical hacking practice (Kali Linux + vulnerable VMs) — this is literally how most people learn practical hacking safely and legally.
- **Segmentation and hardening choices made at setup time** are the same principles auditors check for during a network security assessment.

---

## Quick Revision Points
- LAN setup = topology + cabling/WiFi + IP addressing + gateway + DNS + testing.
- Security must be built in from setup: VLAN segmentation, changed default credentials, deny-by-default firewall rules, DHCP hardening.
- Static IPs suit servers/network devices; DHCP suits general end-user devices — both need proper documentation/monitoring.
- A home ethical hacking lab must be fully isolated (host-only/internal virtual networks) from your real production LAN and the Internet.
- Basic CLI tools (ipconfig, ping, arp, netstat, nslookup) are used both for legitimate setup/troubleshooting and for security diagnostics.


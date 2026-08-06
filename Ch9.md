# Chapter 9 — How to Prepare Cable
### (Cybersecurity / Ethical Hacking Perspective)

This is a hands-on/practical chapter. Even though cable crimping seems purely physical/technical, it matters for security professionals in lab-building, physical pentesting, and understanding hardware implants.

---

## 1. Tools Needed
- **RJ45 connectors**
- **Cat5e/Cat6 UTP cable**
- **Crimping tool**
- **Cable tester** (LAN tester)
- **Wire stripper**

---

## 2. Standard Wiring Schemes: T568A vs T568B

| Pin | T568A | T568B |
|---|---|---|
| 1 | White/Green | White/Orange |
| 2 | Green | Orange |
| 3 | White/Orange | White/Green |
| 4 | Blue | Blue |
| 5 | White/Blue | White/Blue |
| 6 | Orange | Green |
| 7 | White/Brown | White/Brown |
| 8 | Brown | Brown |

- Both standards are functionally equivalent — the difference is just wire order. Enterprises typically standardize on **T568B**.

---

## 3. Types of Cables (Based on Wiring)

### a) Straight-Through Cable
- **Wiring:** Same standard on both ends (T568B–T568B, or T568A–T568A).
- **Use case:** Connecting **different** device types — PC to switch, switch to router.
- **Most common cable type in real networks today** (modern NICs auto-detect, but this remains the standard convention).

### b) Crossover Cable
- **Wiring:** One end T568A, other end T568B.
- **Use case:** Connecting **same** device types directly — PC to PC, switch to switch (older hardware without Auto-MDI-X).
- **Security relevance:** Useful for building isolated point-to-point test labs (e.g., connecting an attack machine directly to a target machine without a switch in between, keeping traffic isolated for analysis).

### c) Rollover Cable (Console Cable)
- **Use case:** Connecting to a device's console port (e.g., Cisco router/switch CLI access) — not used for standard data transmission.
- **Security relevance:** Physical console access is one of the **highest-privilege access methods** to a network device — often bypasses network-based authentication (part of why physical security of network closets matters so much).

---

## 4. Crimping Process (Summary Steps)

1. Strip the outer cable jacket (~1 inch).
2. Untwist and arrange the 8 wires per chosen standard (T568A or T568B).
3. Trim wires evenly and insert into RJ45 connector in correct order.
4. Crimp using the crimping tool to secure the pins.
5. Test using a cable tester to confirm all 8 pins register correctly on both ends.

---

## 5. Security Relevance of Cable Preparation Skills

### a) Building Your Own Pentest Lab
- Understanding cabling lets you build isolated physical lab environments — critical for safely testing exploits, malware, or network attacks without risking production networks.

### b) Recognizing Physical Implants
- Attackers sometimes use **rogue devices** (LAN Turtle, Packet Squirrel, Raspberry Pi implants) that are physically wired inline into a network — recognizing normal vs suspicious cabling/hardware in a server room or office is part of physical security awareness.
- A tampered or unusually placed cable/connector (e.g., an inline dongle between a PC and the wall jack) can be a red flag during a physical security audit.

### c) Cable Testing = Basic Network Troubleshooting for Security Work
- Before assuming a "network is down" is a cyberattack (DoS), physical layer troubleshooting (bad cable, bad crimp) rules out the simplest explanation first — an important part of incident response triage (don't jump to "we're under attack" before checking Layer 1).

### d) Console/Rollover Cable Access
- Physical console access to routers/switches (via rollover cable) is a **critical access control point** — if a network closet is unlocked, anyone can plug in a laptop and gain admin access to core devices, bypassing all network-based security controls.

---

## Quick Revision Points
- T568A and T568B are the two wiring standards; enterprises typically use T568B.
- Straight-through cable = connects different devices (PC–switch); Crossover = connects same devices (PC–PC).
- Rollover/console cable = direct CLI access to network devices — a high-privilege physical access point.
- Cable/crimping skills matter for: building safe pentest labs, recognizing rogue physical implants, and correctly triaging "is this a cyberattack or just a bad cable" during incident response.
- Physical security of cabling and network closets is a foundational (and often overlooked) part of overall network security.

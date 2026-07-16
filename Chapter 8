# Chapter 8 — Transmission Mode and Transmission Media
### (Cybersecurity / Ethical Hacking Perspective)

This chapter covers **how data physically moves** (transmission mode) and **what it moves through** (transmission media). Both determine how easy or hard it is for an attacker to intercept, tap, or disrupt communication.

---

## 1. Transmission Modes (Direction of Data Flow)

| Mode | Description | Example | Security Relevance |
|---|---|---|---|
| **Simplex** | One-way only (sender ≠ receiver ever) | Keyboard to CPU, radio broadcast | Limited attack surface (no return channel) but no error feedback either |
| **Half-Duplex** | Two-way, but one direction at a time | Walkie-talkies | Timing-based attacks possible during "turn-taking" |
| **Full-Duplex** | Two-way, simultaneous | Telephone calls, most modern networks (Ethernet) | Standard for most attacks (MITM requires full-duplex interception of both streams) |

> **Security note:** Most modern MITM attacks (ARP spoofing, SSL stripping) rely on the network being full-duplex — the attacker intercepts, reads/modifies, and forwards traffic in both directions in real time.

---

## 2. Transmission Media — Guided (Wired)

### a) Twisted Pair Cable (UTP/STP)
- **Description:** Copper wires twisted together to reduce interference; most common LAN cabling (Cat5e, Cat6, Cat6a).
- **Security relevance:**
  - Physically tappable if attacker gains local access (inline taps, splitters).
  - **UTP (Unshielded)** more susceptible to electromagnetic eavesdropping (TEMPEST-style attacks) than **STP (Shielded)**.
  - Common medium in the "internal LAN" a pentester targets during on-site engagements.

### b) Coaxial Cable
- **Description:** Single copper conductor with shielding; used in older Ethernet (10BASE2) and cable TV/internet.
- **Security relevance:** Largely legacy; shielding somewhat reduces eavesdropping risk vs UTP, but physical tapping still possible.

### c) Fiber Optic Cable
- **Description:** Transmits data as light pulses through glass/plastic fibers.
- **Security relevance:**
  - Much harder to tap than copper (no electromagnetic emissions), but **not immune** — fiber tapping devices exist (bending the fiber to leak light, or splicing).
  - High-security environments (banks, government) often prefer fiber for exactly this reason.
  - Extremely high bandwidth — cutting it is a devastating physical DoS due to how much traffic it typically carries (backbone links).

---

## 3. Transmission Media — Unguided (Wireless)

### a) Radio Waves
- **Description:** Used in WiFi, Bluetooth, cellular.
- **Security relevance:** Broadcast in all directions — inherently interceptable by anyone in range (basis of WiFi sniffing, Bluetooth attacks).

### b) Microwave
- **Description:** Point-to-point line-of-sight transmission (used in some backhaul/ISP links).
- **Security relevance:** Requires line-of-sight interception equipment — harder to intercept than WiFi but not impossible for a determined/well-resourced attacker.

### c) Infrared
- **Description:** Short-range, line-of-sight (old TV remotes, some older device pairing).
- **Security relevance:** Very limited range/attack surface; mostly historical relevance today.

### d) Satellite
- **Description:** Long-distance communication via orbiting satellites.
- **Security relevance:** Historically weak/no encryption on some satellite links has enabled real-world interception of satellite internet/TV traffic (documented in security research).

---

## 4. Guided vs Unguided — Security Comparison

| Aspect | Guided (Wired) | Unguided (Wireless) |
|---|---|---|
| Interception | Requires physical access/tap | Requires only proximity (no physical access) |
| Range | Limited by cable length | Broadcasts in open air (larger uncontrolled area) |
| Ease of Attack | Harder (physical presence needed) | Easier (passive sniffing possible from a distance) |
| Common Attacks | Cable tapping, splicing | WiFi sniffing, deauth attacks, Bluetooth attacks, jamming |

> **Key takeaway:** Wireless media dramatically lowers the bar for an attacker — no physical access to the building is needed, just proximity. This is why wireless security (covered later in Ch.13) gets its own dedicated chapter.

---

## 5. Why This Matters for Ethical Hacking

- **Physical penetration tests** assess exactly this — can an attacker access a network port, tap a cable, or plant a rogue device?
- **Wireless assessments** assume unguided media is inherently exposed and test encryption/authentication as the only real defense.
- **Choosing attack tools:** Wired MITM (ARP spoofing) vs wireless MITM (evil twin, deauth) depend entirely on the transmission medium in use.

---

## Quick Revision Points
- Simplex/Half-Duplex/Full-Duplex describe direction of flow; most MITM attacks assume full-duplex.
- Guided media (twisted pair, coaxial, fiber) requires physical access to intercept — fiber is hardest to tap.
- Unguided media (radio, microwave, infrared, satellite) is interceptable via proximity alone — far easier to attack passively.
- Wireless is the biggest "easy interception" risk in modern networks — this is why WiFi security gets dedicated focus later in the course.

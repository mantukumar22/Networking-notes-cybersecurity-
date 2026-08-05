# Chapter 5 — Network Topology
### (Cybersecurity / Ethical Hacking Perspective)

Topology = the **physical or logical layout** of a network. For a security professional, topology tells you where the choke points, single points of failure, and easiest lateral-movement paths are — before you even run a tool.

---

## 1. Bus Topology

- **Layout:** All devices connected to a single central cable (backbone).
- **How it works:** Data travels along the cable; every device receives it but only the intended recipient processes it.
- **Security relevance:**
  - Same weakness as a hub — any device (or attacker) tapped into the cable can see all traffic.
  - Single cable failure = entire network down (easy DoS via physical access).
  - Rare today, mostly legacy/historical relevance.

---

## 2. Star Topology

- **Layout:** All devices connect to a central device (switch/hub).
- **Security relevance:**
  - **Most common topology in real networks today.**
  - Central device (switch) becomes the **single point of failure** — compromise or DoS the switch, and the whole segment goes down.
  - Easier to monitor/secure centrally (mirror ports for IDS, centralized logging) — but also a single juicy target for attackers.

---

## 3. Ring Topology

- **Layout:** Devices connected in a closed loop; data travels in one (or both) direction(s) around the ring.
- **Security relevance:**
  - One broken link/device can disrupt the whole ring (unless dual-ring/redundant).
  - Rare in modern LANs (was common in Token Ring networks); more relevant in some legacy industrial/SCADA environments — worth knowing for OT/ICS security contexts.

---

## 4. Mesh Topology

- **Layout:** Every device connects to every other device (full mesh) or to several others (partial mesh).
- **Security relevance:**
  - Highly resilient — no single point of failure (good for defenders: hard to fully DoS).
  - But **larger attack surface** — many more paths/links to secure and monitor.
  - Common in WANs, ISP backbones, and resilient critical infrastructure.

---

## 5. Tree Topology

- **Layout:** Hierarchical — combination of star topologies connected via a bus-like backbone.
- **Security relevance:**
  - Common in large enterprise networks (departments as separate star networks, connected to a core).
  - Compromising a higher-level (core/root) node gives access to all branches below it — a key concept in understanding **network segmentation** and why compromising a core switch/router is catastrophic.

---

## 6. Hybrid Topology

- **Layout:** Combination of two or more topologies (e.g., star-bus, star-mesh).
- **Security relevance:**
  - Reflects most real-world enterprise networks — segmented into zones (DMZ, internal LAN, guest WiFi) using different topology types combined.
  - Understanding hybrid layouts is essential for **network segmentation analysis** during a pentest — where are the boundaries, and are they enforced?

---

## 7. Physical vs Logical Topology

| Type | Meaning | Security Relevance |
|---|---|---|
| **Physical Topology** | Actual physical layout/cabling of devices | Relevant to physical security assessments, wiretapping risk |
| **Logical Topology** | How data actually flows regardless of physical layout (e.g., VLANs create logical segments over physical star topology) | Relevant to understanding VLAN hopping, segmentation bypass |

> **Key insight:** A network can be physically a star (everything plugged into switches) but logically segmented into multiple VLANs — attackers/pentesters need to understand both to find where "logical" boundaries can be broken (VLAN hopping, trunk port abuse).

---

## 8. Why Topology Matters for a Pentester/Analyst

- **Network diagrams** (topology maps) are often one of the first things gathered in reconnaissance (via tools like Nmap topology scans, or social engineering to get network diagrams).
- **Identifying single points of failure** tells you where a DoS attack has maximum impact.
- **Identifying segmentation** (or lack thereof) tells you how far lateral movement can go after an initial foothold.
- Poor segmentation (flat network, "everything is one big star/bus logically") is one of the **most common findings in real-world pentest reports** — it's why ransomware spreads so fast in poorly segmented networks.

---

## Quick Revision Points
- Bus/Ring = legacy, single point of failure, easy to disrupt physically.
- Star = most common today; central switch is the key point of failure/monitoring.
- Mesh = resilient but larger attack surface; common in critical infrastructure/WANs.
- Tree/Hybrid = reflects real enterprise segmentation (departments, DMZ, guest networks).
- Physical vs Logical topology distinction is essential for understanding VLANs and segmentation bypass attacks.
- Good segmentation = contains breaches; poor segmentation = a single foothold compromises everything.


# Site-to-Site GRE Tunnel Implementation 🌐

This repository contains the configuration and topology details for a Site-to-Site GRE (Generic Routing Encapsulation) Tunnel built using Cisco Packet Tracer.

## 📍 Topology Map
![Network Topology](topology-image.png)

## 🏗️ Architecture Overview
* **Internal LAN A:** `192.0.0.0/24`
* **Internal LAN B:** `180.0.0.0/24`
* **WAN Underlay:** `50.0.0.0/24` and `75.0.0.0/24`
* **Tunnel Subnet:** `1.1.1.0/8` (Classless implementation)

---

## 🛠️ Configuration Highlights

### Router 1 (Branch A)
- Established **Tunnel0** with source `Fa0/1` and destination `75.0.0.2`.
- Applied static route to the remote LAN via the Tunnel IP: `1.1.1.2`.

### Router 3 (Branch B)
- Mirror configuration pointing back to R1's physical IP: `50.0.0.2`.
- Established the return path for the `192.0.0.0/24` network.

---

## 🔍 Verification & Testing
Successful connectivity was verified using the following methods:

1.  **ICMP Connectivity:** `ping` (100% success rate after initial ARP resolution).
2.  **Path Analysis:** `tracert` (Confirmed that the intermediate ISP hop is logically hidden, proving encapsulation).
3.  **Interface State:** `show ip interface brief` (Confirmed Tunnel0 status is `up/up`).

## 🎓 Skills Demonstrated
* **L3 VPN Logic:** Understanding GRE encapsulation.
* **Static Routing:** Managing both Underlay and Overlay routing tables.
* **Troubleshooting:** Resolving Next-Hop errors and stateless interface issues.
* **IP Management:** Applying CIDR and Subnetting principles.

---

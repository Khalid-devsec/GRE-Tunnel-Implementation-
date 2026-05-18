# Site-to-Site GRE-Tunnel-Implementation

This repository contains the configuration and topology details for a Site-to-Site GRE (Generic Routing Encapsulation) Tunnel built using Cisco Packet Tracer.

## Topology Overview
- **Internal LAN A:** 192.0.0.0/24
- **Internal LAN B:** 180.0.0.0/24
- **WAN Underlay:** 50.0.0.0/24 and 75.0.0.0/24
- **Tunnel Subnet:** 1.1.1.0/8 (Classless implementation)

## Configuration Highlights

### Router 1 (Branch A)
- Established Tunnel0 with source `Fa0/1` and destination `75.0.0.2`.
- Applied static route to the remote LAN via the Tunnel IP: `1.1.1.2`.

### Router 3 (Branch B)
- Mirror configuration pointing back to `50.0.0.2`.
- Established the return path for the 192.0.0.0/24 network.

## Verification
Successful connectivity was verified using:
1. `ping` (100% success rate after initial ARP).
2. `tracert` (Confirmed that the intermediate ISP hop is logically hidden).
3. `show ip interface brief` (Confirmed Tunnel0 status is up/up).

## Skills Demonstrated
- Static Routing
- GRE Tunneling
- Troubleshooting Next-Hop Errors
- CIDR & Subnetting

# RCOMP 2025-2026 Project 1 – Sprint 3 – Member 1241210

## Introduction

This document details the implementation of advanced network features for **Sprint 3** concerning **Terminal 3**. The focus of this sprint was the transition from static to dynamic routing, the implementation of Voice over IP (VoIP) services, the establishment of a global DNS hierarchy, and perimeter security through NAT and Access Control Lists (ACLs).

As the Sprint Master for this period, I was also responsible for the Root Domain authority and the final integration of all terminals into the `campus.pkt` file.

## 1. Dynamic Routing (OSPFv2)

Static routing from Sprint 2 has been removed and replaced by **OSPF**.
- **Backbone Area (Area 0):** Includes the 10.80.127.0/24 network (VLAN 806).
- **Local Area (Area 3):** Includes all internal subnets for Terminal 3 (10.80.32.0/19).
- **Security:** Configured `passive-interface default`, allowing OSPF traffic only on the Backbone-facing interface to prevent topology exposure in user networks.

## 2. Infrastructure Services (DHCPv4)

The **01_RT_03_01** router was configured as the DHCP server for local networks:
- **Configured Pools:** `T3_USERS` (VLAN 812), `T3_WIFI` (VLAN 813), and `T3_VOIP` (VLAN 814).
- **Option 150:** Implemented in the VoIP pool to provide the TFTP server address (the router itself: 10.80.48.1) to the Cisco 7960 IP phones.
- **Exclusions:** IPs from .1 to .10 are reserved for management and static servers.

## 3. VoIP (Cisco Telephony Service)

Implementation of a local telephony exchange with inter-terminal call support:
- **Prefix:** 3XXX (Terminal 3).
- **Capacity:** 8 phones configured and distributed by services (Arrivals, Departures, Admin, etc.) based on the established range schema.
- **Dial-Peers:** Configured voice routing for Terminal 2 (2XXX) and Terminal 5 (5XXX) via IPv4.
- **Switch Configuration:** Ports set to access mode (VLAN 812) with a voice overlay (VLAN 814).

## 4. Hierarchical DNS

Configured the server **10.80.50.2** as the authority for the root domain `rcomp-25-26-2DJ-g4.pt`:
- **Local Zone:** Management of the `t3.rcomp-25-26-2DJ-g4.pt` subdomain.
- **Glue Records:** Created **A** and **NS** records to delegate authority to subdomains managed by team members (Henri/T2 and Rodrigo/T5).
- **Services:** Includes `www`, `web`, `server1`, and `ns` records for the DMZ servers.

## 5. NAT and Security (Static Firewall)

- **Static NAT:** Mapped the Backbone public IP (10.80.127.3) to the internal Web Server (10.80.50.3) for ports 80 and 443.
- **Firewall ACL:** Implemented a restrictive security policy on the inbound interface:
    - Permitted OSPF and ICMP traffic.
    - Permitted DNS (UDP 53) and Web traffic (TCP 80/443) to the DMZ.
    - Blocked external IP Spoofing.
    - Implicitly denied all other unauthorized traffic to the DMZ and Router.

## 6. Global Integration (Campus Integration)

As the final subtask, I merged individual works into the `campus.pkt` file. Integration ensured Trunk link continuity on the Backbone and OSPF convergence across the three terminal routers.

---
**Miguel Ribeiro (1241210)**
*Sprint Master - RCOMP 2025/2026*
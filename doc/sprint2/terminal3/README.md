# RCOMP 2025-2026 Project 1 – Sprint 2 – Member 1241210 folder

## Introduction

This document describes the implementation of the layer two and layer three network simulation developed for **Terminal 3**, using Cisco Packet Tracer.

The simulation represents the structured cabling project developed in Sprint 1, including cross-connects modeled as switches, a router for inter-VLAN routing, and end devices associated with each VLAN. It also includes integration with the Campus Backbone network and connectivity to the Internet through the Main Router located in Terminal 2, as required in the project specification.

## Terminal 3 Switch and Router Inventory

- **Main Router:** 01_RT_03_01 (Model Cisco 2811)
- **IC (Intermediate Cross-connect):** 01_SW_IC_03_01 (Model Switch-PT)
- **HCs (Horizontal Cross-connects):** Model Switch-PT distributed across floors.
- **End Devices:** PCs, Laptops, Servers, VoIP phones, Tablets, Smartphone, and Printers.

## Terminal 3 IPv4 Configuration

### Subnets Table
The IPv4 block assigned to Terminal 3 is **10.80.32.0/19**. Following the required hierarchy of needs, the addressing was established as follows:

| VLAN ID |  VLAN Name  | IPs Needed | Subnet Mask | Default Gateway  | First Usable IP | Last Usable IP |
|:-------:|:-----------:|:----------:|:-----------:|:----------------:|:---------------:|:--------------:|
| 812 |  T3_USERS   |    950     | 255.255.252.0 (/22) |    10.80.32.1    | 10.80.32.2 | 10.80.35.254 |
| 813 |   T3_WIFI   |    1500    | 255.255.248.0 (/21) |    10.80.40.1    | 10.80.40.2 | 10.80.47.254 |
| 814 |   T3_VOIP   |    350     | 255.255.254.0 (/23) |    10.80.48.1    | 10.80.48.2 | 10.80.49.254 |
| 815 | T3_SERVERS  |    150     | 255.255.255.0 (/24) |    10.80.50.1    | 10.80.50.2 | 10.80.50.254 |

---

## Layer 2 Configuration

### VTP and VLANs
- **VTP Domain:** All switches are configured with the mandatory domain `rc2526djg4`.
- **VTP Modes:** The MC switch acts as the **VTP Server**, propagating the VLAN database (806 to 826) to the IC and HCs configured as **VTP Clients**.
- **Trunking:** All inter-switch links use 802.1Q encapsulation, with **VLAN 820** configured as the **Native VLAN** for security purposes.

### Switch Management (VLAN 807 - SWITCHES_DMZ)
Each switch in Terminal 3 has an IP address assigned in **VLAN 807** to allow remote management. The IPs were assigned within the range reserved for Terminal 3 (**10.80.96.30 to 10.80.96.49**) with the mask **255.255.254.0**.

### Redundancy and Spanning Tree
Redundancy was implemented between the ICs to ensure network availability. To ensure a stable Spanning Tree Protocol (STP) convergence during the global integration of the three terminals, the hierarchy was adjusted by removing one HC from Terminal 2 and Terminal 3. This prevented complex loops in the simulation environment while maintaining core functional redundancy.

---

## Layer 3 Configuration

### Inter-VLAN Routing
Routing between Terminal 3 internal VLANs is performed by the **01_RT_03_01** router using sub-interfaces (Router-on-a-Stick).

### Backbone Integration and Static Routing
To allow communication with other terminals and the Internet, a **Default Static Route** was implemented pointing to the Main Router (Backbone Gateway):
- **Route:** `ip route 0.0.0.0 0.0.0.0 10.80.127.254`

The router's interface connected to the Backbone is configured with the IP `10.80.127.3` (VLAN 806).

---

## Campus-Wide Simulation (Integration of 3 Terminals)

The global simulation demonstrates full interconnectivity across the airport campus:
1. **Inter-Terminal Traffic:** A device in Terminal 3 can communicate with servers in Terminal 2 or Terminal 5 by traversing the Backbone (VLAN 806).
2. **Internet Access:** All internet-bound traffic from T3 is forwarded via the default route to the Main Router in Terminal 2, which then sends it to the ISP Router at `89.77.67.9`.
3. **DNS Services:** End devices in T3 use the local server (`10.80.50.2`) for name resolution, which is configured to resolve external addresses (e.g., `www.google.com`) pointing to simulated internet servers.

---

## Testing and Validation

- **Ping Tests:** Connectivity successfully validated between all internal VLANs and to the Backbone Gateway (`10.80.127.254`).
- **Traceroute:** Confirmed the path taken by packets from T3 devices to the ISP, crossing the local router and the campus backbone.
- **Web Browsing:** Functional DNS resolution and HTTP access to simulated web servers.
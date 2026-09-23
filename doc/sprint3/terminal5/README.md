# RCOMP 2025-2026 Project 1 – Sprint 3 – Member 1241216

## Introduction

This document details the implementation of advanced network features for **Sprint 3** concerning **Terminal 5**. The focus of this sprint was the migration from static to dynamic routing, the deployment of Voice over IP (VoIP) services, the establishment of a hierarchical DNS infrastructure, and the implementation of security mechanisms using ACLs.

Terminal 5 was integrated into the campus backbone through OSPF, allowing communication with all other terminals while maintaining network segmentation and security policies.

## 1. Dynamic Routing (OSPFv2)

Static routing from Sprint 2 was removed and replaced with **OSPFv2**.

* **Backbone Area (Area 0):** Includes the inter-router network `10.80.127.0/24` (VLAN 806).
* **Local Area (Area 5):** Includes all internal subnets for Terminal 5 (`10.80.64.0/19`).
* **Security:** Configured `passive-interface default`, allowing OSPF adjacency only through the Backbone-facing interface.
* **Convergence:** Verified through successful neighbor establishment with Terminal 2 and Terminal 3 routers.

## 2. Infrastructure Services (DHCPv4)

The router **01_RT_05_01** was configured as the DHCP server for Terminal 5.

### Configured DHCP Pools

* **T5_USERS** – VLAN 816 (`10.80.80.0/21`)
* **T5_WIFI** – VLAN 817 (`10.80.64.0/20`)
* **T5_VOIP** – VLAN 818 (`10.80.88.0/23`)

### Additional DHCP Features

* **DNS server assignment** configured for all clients.
* **Option 150** configured in the VoIP pool to provide the TFTP/CME server address (`10.80.88.1`) to Cisco IP phones.
* **Excluded addresses** reserved for routers, servers, and management devices.

## 3. VoIP (Cisco Telephony Service)

A local Cisco CME telephony service was implemented in Terminal 5.

### VoIP Characteristics

* **Prefix:** `5XXX`
* **IP Phones:** Cisco 7960 devices
* **Voice VLAN:** VLAN 818
* **CME Address:** `10.80.88.1`

### Telephony Features

* Internal calls between local extensions.
* Inter-terminal calls through VoIP dial-peers.
* Automatic phone registration through DHCP and TFTP.

### Dial-Peers

* Calls to Terminal 2 (`2XXX`) routed through `10.80.127.2`
* Calls to Terminal 3 (`3XXX`) routed through `10.80.127.3`

### Switch Configuration

Switch access ports connected to IP phones were configured with:

* Access VLAN 816 (data)
* Voice VLAN 818 (VoIP)
* PortFast enabled

## 4. Hierarchical DNS

The server `10.80.90.10` was configured as the DNS authority for the subdomain:

`t5.rcomp-25-26-2DJ-g4.pt`

### DNS Features

* Local resolution for Terminal 5 services.
* `A` records created for web and DNS services.
* `NS` delegation configured to integrate with the global DNS hierarchy.
* Resolution of remote domains from Terminal 2 and Terminal 3 validated successfully.

### Main DNS Records

* `www.t5.rcomp-25-26-2DJ-g4.pt`
* `ns.t5.rcomp-25-26-2DJ-g4.pt`

## 5. Security and Access Control (ACLs)

Security policies were implemented using extended ACLs.

### ACL Objectives

* Permit DNS traffic to the DNS server.
* Permit HTTP/HTTPS traffic to the web server.
* Restrict unauthorized access to the server VLAN.
* Separate user traffic from infrastructure services.

### Firewall Behavior

* ICMP traffic to servers may be blocked while HTTP services remain accessible.
* Web services remain reachable through the browser even when ping is denied.
* ACLs applied inbound on VLAN interfaces.

## 6. Campus Integration

Terminal 5 was successfully integrated into the complete campus infrastructure.

### Integration Validation

* OSPF neighbors established with all terminal routers.
* Successful route propagation between all areas.
* DNS resolution validated across terminals.
* Inter-terminal VoIP calls validated.
* Web services reachable from remote terminals.

## 7. Validation and Testing

The following tests were successfully performed:

* OSPF adjacency validation (`show ip ospf neighbor`)
* Dynamic route propagation (`show ip route`)
* DHCP lease assignment (`show ip dhcp binding`)
* VoIP registration (`show ephone`)
* DNS resolution using FQDNs
* HTTP access to all web servers
* Inter-terminal ping and routing tests
* Inter-terminal VoIP call testing

---

**Rodrigo Guimarães (1241442)**
*RCOMP 2025/2026*

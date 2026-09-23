
# RCOMP 2025-2026 Project 1 – Sprint 2 – Member 1241442 folder

# Introduction

This document describes the implementation of the layer two and layer three network simulation developed for **Terminal 5**, using Cisco Packet Tracer.

The simulation represents the structured cabling project developed in Sprint 1, including cross-connects modeled as switches, a router for inter-VLAN routing, and end devices associated with each VLAN. It also includes integration with the Campus Backbone network and connectivity to the ISP through Terminal 2, as required in the project specification.

---

# Terminal 5 IPv4 Configuration

## Subnets Table

| VLAN ID | VLAN            | Number of IPs | Subnet Mask   | Default Gateway | First Usable IP | Last Usable IP |
|:-------:|-----------------|---------------|---------------|-----------------|-----------------|----------------|
|   806   | CAMPUS_BACKBONE | 254           | 255.255.255.0 | 10.80.127.254   | 10.80.127.1     | 10.80.127.254  |
|   807   | SWITCHES_DMZ    | 510           | 255.255.254.0 | 10.80.97.254    | 10.80.96.1      | 10.80.97.254   |
|   816   | T5_USERS        | 2046          | 255.255.248.0 | 10.80.80.1      | 10.80.80.1      | 10.80.87.254   |
|   817   | T5_WIFI         | 4094          | 255.255.240.0 | 10.80.64.1      | 10.80.64.1      | 10.80.79.254   |
|   818   | T5_VOIP         | 510           | 255.255.254.0 | 10.80.88.1      | 10.80.88.1      | 10.80.89.254   |
|   819   | T5_SERVERS      | 254           | 255.255.255.0 | 10.80.90.1      | 10.80.90.1      | 10.80.90.254   |

---

## IPv4 Network Addresses Establishment

The IPv4 block assigned to Terminal 5 is:

```text
10.80.64.0/19
```

This block was subdivided according to the number of required hosts for each VLAN:

* User outlets: 1900 nodes → /21
* Wi-Fi: 4000 nodes → /20
* VoIP: 500 nodes → /23
* Servers DMZ: 200 nodes → /24

This subdivision ensures that each network supports the required number of devices while maintaining efficient address allocation.

---

# Layer 2 Configuration

## Network Structure

The network is organized according to the structured cabling model:

* IC (Intermediate Cross-connect) – main switch of the terminal
* HC (Horizontal Cross-connect) – intermediate distribution switches
* CP (Consolidation Points) – access switches

All switches were interconnected according to the logical topology, including redundant links.

---

## VLAN Configuration

All VLANs required by the project were created and made available on every switch, including VLANs from other terminals.

The VLAN database was propagated using VTP.

---

## VTP Configuration

* All switches configured with the same VTP domain
* One switch configured as VTP Server
* Remaining switches configured as VTP Clients

This ensured consistency of VLAN configuration across the entire network.

---

## Trunk Configuration

All inter-switch links and switch-router links were configured as trunk ports:

```bash
interface faX/X
 switchport mode trunk
 switchport trunk native vlan 820
```

This allows all VLAN traffic to be transported between switches and to the router.

---

## Spanning Tree Protocol

Spanning Tree Protocol (STP) was kept enabled on all switches to prevent loops caused by redundant links.

No manual STP configuration was required.

---

# Layer 3 Configuration

## Router Configuration

A Cisco 2811 router was used to perform inter-VLAN routing using the router-on-a-stick approach.

Subinterfaces were configured as follows:

```bash
interface fa0/0.X
 encapsulation dot1Q X
 ip address ...
```

Each subinterface corresponds to one VLAN.

---

## Static Routing

Static routes were configured to allow communication:

* between VLANs within the terminal
* between different terminals through the backbone

Default route:

```bash
ip route 0.0.0.0 0.0.0.0 10.80.127.254
```

---

# Switches Management (Switches DMZ)

Each switch was configured with an IP address in VLAN 807:

```bash
interface vlan 807
 ip address 10.80.96.X 255.255.254.0
 no shutdown
```

Default gateway:

```bash
ip default-gateway 10.80.97.254
```

This allows remote management of switches through a dedicated management network.

---

# End Devices Configuration

Each VLAN contains at least one end device, as required:

* PC → User VLAN
* Laptop → Wi-Fi VLAN (via Access Point)
* Server → Servers VLAN
* IP Phone → VoIP VLAN
* Management PC → Switches DMZ

Ports were configured as access ports:

```bash
switchport mode access
switchport access vlan X
```

For VoIP:

```bash
switchport voice vlan X
```

---

# Internet Connectivity

Internet access is provided through Terminal 2.

The ISP router is reachable at:

```text
89.77.67.9
```

The connection was validated using:

```bash
ping 89.77.67.9
tracert 89.77.67.9
```

Traceroute result confirms the path:

```text
Terminal 5 → Backbone → Router Central → ISP
```

---

# Testing and Validation

The following tests were successfully performed:

* Intra-VLAN communication
* Inter-VLAN communication
* Communication between terminals
* Connectivity to the ISP
* Traceroute validation

All expected network behaviors were confirmed.

---

# Conclusion

The network simulation for Terminal 5 was successfully implemented according to the project requirements.

The solution includes:

* complete Layer 2 configuration with VLANs, VTP, and trunking
* Layer 3 routing using router-on-a-stick
* static routing across the campus backbone
* functional integration with other terminals
* validated connectivity to the ISP

The implemented solution meets all the requirements defined for Sprint 2.

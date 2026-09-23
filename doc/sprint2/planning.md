RCOMP 2025-2026 Project 1 - Sprint 2 planning
===========================================
### Sprint master: 1241210 ###

# 1. Sprint's backlog #

| Task  | Member responsible for the task | Task description                                                                                                                                                                                                |
|-------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| T.2.1 | Henri Fontes                    | Development of a layer two and layer three Packet Tracer simulation for Terminal 2 encompassed floors, the campus backbone, and including the internet connection.                                              |
| T.2.2 | Miguel Ribeiro                  | Development of a layer two and layer three Packet Tracer simulation for Terminal 3 encompassed floors and the campus backbone. Integration of every member’s Packet Tracer simulation into a single simulation. |
| T.2.3 | Rodrigo Guimarães               | Development of a layer two and layer three Packet Tracer simulation for Terminal 5 encompassed floors and the campus backbone.                                                                                  |

# 2. Technical decisions and coordination #

### Packet Tracer version ###
**9.0.0**

### Device: NN_DD_CC_TT_LL  ###

* NN is the number of the device on Terminal / Level.
* DD is the device type (e.g., SW for switch, RT for router, etc.).
* CC is Cross-Connect Device (e.g., IC Intermediate-Connector, HC Horizontal Connector, etc.).
* TT is the terminal number (e.g., 02 for Terminal 2).
* LL is the level number (e.g., 01 for Level 1).

### Mandatory team data

Class: *2DJ*  
Team number: *4*

#### VTP domain name
The mandatory VTP domain name for this team is:

*rc2526djg4*

#### VLAN ID range
The mandatory VLAN ID range for this team is:

*806 to 826*

#### Team IPv4 block
The mandatory IPv4 block for this team is:

*10.80.0.0/17*

#### ISP router IPv4 node address
The mandatory ISP router IPv4 address for this team is:

*89.77.67.9/30*

---

## Layer 2 planning

### Default VLAN
The team keeps the Cisco default VLAN:

- **VLAN 1 — DEFAULT**

### Native VLAN
The team defines the following native VLAN for trunk links:

- **VLAN 820 — NATIVE_UNUSED**

This VLAN will be used only as native VLAN on trunk links and will not be used by end devices.

### Parking VLAN for unused ports
The team defines:

- **VLAN 821 — PARKING_BLACKHOLE**

Unused switch ports should be assigned to this VLAN and administratively shut down whenever possible.

### Reserved VLAN
The team reserves:

- **VLAN 822 — RESERVED**

### VLAN database
Since this team only includes **T2, T3 and T5**, the common VLAN database is:

| VLAN ID | VLAN Name         |
|---------|-------------------|
| 1       | DEFAULT           |
| 806     | CAMPUS_BACKBONE   |
| 807     | SWITCHES_DMZ      |
| 808     | T2_USERS          |
| 809     | T2_WIFI           |
| 810     | T2_VOIP           |
| 811     | T2_SERVERS        |
| 812     | T3_USERS          |
| 813     | T3_WIFI           |
| 814     | T3_VOIP           |
| 815     | T3_SERVERS        |
| 816     | T5_USERS          |
| 817     | T5_WIFI           |
| 818     | T5_VOIP           |
| 819     | T5_SERVERS        |
| 820     | NATIVE_UNUSED     |
| 821     | PARKING_BLACKHOLE |
| 822     | RESERVED          |

All these VLANs must exist on every switch in every terminal.

---

## Layer 3 planning

### IPv4 Configuration for the Airport

The IPv4 network address for the Campus Backbone network is:

**10.80.127.0/24**

- **Terminal 2 Router IPv4 address:** 10.80.127.2
- **Terminal 3 Router IPv4 address:** 10.80.127.3
- **Terminal 5 Router IPv4 address:** 10.80.127.5
- **Main Router IPv4 address:** 10.80.127.254

The IPv4 network address for the Switches DMZ network is:

**10.80.96.0/23**

- **Range for Terminal 2 Switches:** 10.80.96.20 – 10.80.96.29
- **Range for Terminal 3 Switches:** 10.80.96.30 – 10.80.96.49
- **Range for Terminal 5 Switches:** 10.80.96.50 – 10.80.96.70

### Terminal 2

**IPv4 network addresses block: 10.80.0.0/19**

| VLAN |   Use   |  Network   |   Subnet Mask   | Network Mask | Default Gateway  |          IP Range          |
|:----:|:-------:|:----------:|:---------------:|:------------:|:----------------:|:--------------------------:|
| 808  |  Users  | 10.80.0.0  |  255.255.252.0  |     /22      |   10.80.3.254    |  10.80.0.0 to 10.80.3.255  |
| 809  |  Wi-Fi  | 10.80.16.0 |  255.255.248.0  |     /21      |   10.80.23.254   | 10.80.16.0 to 10.80.23.255 |
| 810  |  VoIP   | 10.80.8.0  |  255.255.254.0  |     /23      |   10.80.9.254    |  10.80.8.0 to 10.80.9.255  |
| 811  | Servers | 10.80.10.0 | 255.255.255.128 |     /25      |   10.80.10.126   | 10.80.10.0 to 10.80.10.126 |

### Terminal 3

**IPv4 network addresses block: 10.80.32.0/19**

| VLAN |   Use   |  Network   |  Subnet Mask  | Network Mask | Default Gateway |          IP Range          |
|:----:|:-------:|:----------:|:-------------:|:------------:|:---------------:|:--------------------------:|
| 812  |  Users  | 10.80.32.0 | 255.255.252.0 |     /22      |   10.80.32.1    | 10.80.32.1 to 10.80.35.254 |
| 813  |  Wi-Fi  | 10.80.40.0 | 255.255.248.0 |     /21      |   10.80.40.1    | 10.80.40.1 to 10.80.47.254 |
| 814  |  VoIP   | 10.80.48.0 | 255.255.254.0 |     /23      |   10.80.48.1    | 10.80.48.1 to 10.80.49.254 |
| 815  | Servers | 10.80.50.0 | 255.255.255.0 |     /24      |   10.80.50.0    | 10.80.50.1 to 10.80.50.254 |

### Terminal 5

**IPv4 network addresses block: 10.80.64.0/19**

| VLAN |   Use   |  Network   |  Subnet Mask   | Network Mask | Default Gateway |          IP Range          |
|:----:|:-------:|:----------:|:--------------:|:------------:|:---------------:|:--------------------------:|
| 816  |  Users  | 10.80.80.0 | 255.255.248.0  |     /21      |   10.80.80.1    | 10.80.80.1 to 10.80.87.254 |
| 817  |  Wi-Fi  | 10.80.64.0 | 255.255.240.0  |     /20      |   10.80.64.1    | 10.80.64.1 to 10.80.79.254 |
| 818  |  VoIP   | 10.80.88.0 | 255.255.254.0  |     /23      |   10.80.88.1    | 10.80.88.1 to 10.80.89.254 |
| 819  | Servers | 10.80.90.0 | 255.255.255.0  |     /24      |   10.80.90.1    | 10.80.90.1 to 10.80.90.254 |

# 3. Subtasks assignment #

* 1241210 - Develop the network simulation for Terminal 3
* 1241442 - Develop the network simulation for Terminal 5
* 1241437 - Develop the network simulation for Terminal 2
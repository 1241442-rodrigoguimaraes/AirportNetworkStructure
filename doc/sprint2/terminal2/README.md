RCOMP 2025-2026 Project 1 – Sprint 2 – Member 1241437 folder
===========================================

## Introduction

This document focuses on the clarification of the structure developed for layer two and layer three Packet Tracer simulation for Terminal 2 encompassed floors. This
simulation includes cross-connect as switches, routers and end devices, all representing the structure cabling project for the same terminal idealized on the first 
Sprint of **RCOMP 2025–2026 Project 1**, also including structures for the Campus Backbone and internet connection to the terminal. 

## Terminal 2 Switch and Router Inventory

- **Main Router:** 02_RT_02_01 (Model 2811)
- **MC:** 01_SW_MC_02_01 (Model Switch-PT)
- **ISP Router:** 01_ISP_02_01 (Model 2811)
- **Cloud:** 01_CD_N_N 
- **DSL Modem:** 01_DSL_02_01 (Model DSL Modem)
- **Terminal 2 Router:** 01_RT_02_01 (Model 2811)
- **IC:** 01_SW_IC_02_01 (Model Switch-PT)
- **HCs First Level:** X_SW_HC_02_01 (Model Switch-PT)
- **HCs Fourth Level:** X_SW_HC_02_04 (Model Switch-PT)

## Terminal 2 IPv4 Configuration

### Subnets Table

| VLAN ID |      VLAN       | Number of available IPs |   Subnet Mask   | Default Gateway | First Usable IP | Last Usable IP |
|:-------:|:---------------:|:-----------------------:|:---------------:|:---------------:|:---------------:|:--------------:|
|   806   | CAMPUS_BACKBONE |           254           |  255.255.255.0  |  10.80.127.254  |   10.80.127.1   | 10.80.127.254  |
|   807   |  SWITCHES_DMZ   |           510           |  255.255.254.0  |  10.80.97.254   |   10.80.96.1    |  10.80.97.254  |
|   808   |    T2_USERS     |          1022           |  255.255.252.0  |   10.80.3.254   |    10.80.0.1    |  10.80.3.254   |
|   809   |     T2_WIFI     |          2046           |  255.255.248.0  |  10.80.23.254   |   10.80.16.1    |  10.80.23.254  |
|   810   |     T2_VOIP     |           510           |  255.255.254.0  |   10.80.9.254   |    10.80.8.1    |  10.80.9.254   |
|   811   |   T2_SERVERS    |           126           | 255.255.255.128 |  10.80.10.126   |   10.80.10.1    |  10.80.10.126  |

---

### VLAN Configuration

The VLAN Database was propagated throughout the switches in the terminal by the VTP protocol. All switches are configured with the same VTP domain (rc2526djg4), and the MC
switch is configured in 'VTP Server' mode while the remaining switches are configured in 'VTP Client mode'. This ensured consistency of VLAN configuration across the entire
network.

All ports responsible for inter-switch links and switch-router links were configured as ´Trunk', which allows all VLAN traffic to be transported between switches and to the
router.

---

### IPv4 Network Addresses Establishment

The division of my IPv4 network addresses block **10.80.0.0/19** was made based on the minimum number of nodes each subnet should support. Those numbers are:

- **User outlets:** 1000 nodes.
- **Wi-Fi:** 2000 nodes.
- **VoIP:** 500 nodes.
- **Servers DMZ:** 100 nodes.

With that in mind, the solution is the division of the network block into four subnetworks with the respective masks: **/22**, **/21**, **/23** and **/25**.
This division supports correctly the number of nodes each subnet should have. 

---

### Static Routing

The routing logic was designed to ensure that Terminal 2 can communicate with the Campus Backbone and the Internet through the Main Router.

#### Terminal 2 Router (Edge Routing)

A Default Static Route was implemented on the Terminal 2 Router. Since the Main Router is the only gateway to the rest of the network and the Internet, all non-local
traffic is forwarded to it.

- **Route:** 0.0.0.0 0.0.0.0
- **Next-Hop:** 10.80.127.254

#### Main Router (Core Routing)

To allow return traffic and inter-terminal communication, the Main Router was configured with a Static Route pointing to the Terminal 2 network block.

- **Destination Network:** 10.80.0.0
- **Mask:** 255.255.224.0 (/19)
- **Next-Hop:** 10.80.127.2

## Internet Connection

Terminal 2 provides an internet connection for the entire campus of the airport. The Internet connection was established through the ISP Router connected to a DSL Modem.
The link between the Main Router and the ISP Router uses the specific public IPv4 address assigned to the team: **89.77.67.9/30**.

The ISP Router is configured with a static route to forward all traffic destined for the 10.80.0.0/17 internal block back to the Main Router.

The Main Router uses its default gateway (0.0.0.0/0) to forward all non-local and non-campus traffic to the ISP Router's interface.

## End Devices Configuration

Each end device is configured with an IPv4 node static address, including a gateway address. The end devices are connected to their respective VLANs:

- **PCs & Laptops:** 808
- **Access Points:** 809
- **VoIPs:** 810
- **Server:** 811

## Remote Management (Switches DMZ)

Each switch in the terminal has an attributed IP address on VLAN 807 at a virtual interface. This subnet is isolated and accessed from a remote dedicated management station.

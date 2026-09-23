# RCOMP 2025-2026 — Project 1: Airport Network Structure

## 🏫 Institutional Information

| Parameter | Information |
| :--- | :--- |
| **Institution** | ISEP (Instituto Superior de Engenharia do Porto) |
| **Degree** | Licenciatura em Engenharia Informática (LEI) |
| **Course** | RCOMP (Redes de Computadores) |
| **Academic Year** | 2025–2026 |
| **Class** | 2DJ |
| **Team Number** | 4 |

---

## 👥 Team Members

| Student ID | Name |
| :--- | :--- |
| **1241442** | Rodrigo Guimarães |
| **1241437** | Henri Fagundes (Henri Fontes) |
| **1241210** | Miguel Ribeiro |

---

## 📖 Project Context & Overview

This project was developed within the scope of the **Computer Networks (RCOMP)** course at ISEP. The goal is to design, implement, and validate a comprehensive enterprise-grade network infrastructure for an international airport comprising multiple terminals (**Terminal 2**, **Terminal 3**, and **Terminal 5**), connected through a robust **Campus Backbone**.

The project was executed across three incremental sprints:
1. **Sprint 1 (Structured Cabling):** Design of structured cabling layouts across all terminal floors (using CAT7 copper and optical fiber for backbones) and distribution spaces (MC, IC, HC, CP).
2. **Sprint 2 (Layer 2 & Layer 3 Simulation):** Implementation of network simulation in Cisco Packet Tracer, defining VLAN databases, VTP domains, trunking, initial static/default routing, and IP addressing blocks (`10.80.0.0/17`).
3. **Sprint 3 (Advanced Services & Integration):** Migration to dynamic routing (OSPFv2), deployment of DHCPv4 servers, VoIP (Cisco CME and IP phones), hierarchical DNS infrastructure, and network security policies using Access Control Lists (ACLs), culminating in the full integrated campus simulation.

---

## 🗂️ Repository Structure

```text
AirportNetworkStructure/
├── README.md                             # Project documentation and details
├── simulations/                          # Cisco Packet Tracer (.pkt) simulation files
│   ├── terminal-2/                       # Terminal 2 simulations (Sprint 2 & 3)
│   ├── terminal-3/                       # Terminal 3 simulations (Sprint 2 & 3)
│   ├── terminal-5/                       # Terminal 5 simulations (Sprint 2 & 3)
│   └── campus/                           # Integrated airport network simulations
├── configs/                              # Cisco IOS running-configurations (Dumps)
│   ├── terminal-2/
│   ├── terminal-3/
│   └── terminal-5/
└── doc/                                  # Sprint planning and review documentation
    ├── sprint1/
    ├── sprint2/
    └── sprint3/
```

---

## 🚀 How to Run & Explore

### Prerequisites
* **Cisco Packet Tracer** (Recommended version: **9.0.0** or higher) to open and interact with simulation files.
* A text editor (such as VS Code) to inspect router and switch configuration dumps in the `configs/` directory.

### Exploring the Simulations
1. Navigate to the `simulations/` directory.
2. Open the integrated campus simulation:
   * `simulations/campus/campus_sprint3_final.pkt`
3. Alternatively, inspect individual terminal simulations under `simulations/terminal-2/`, `simulations/terminal-3/`, or `simulations/terminal-5/`.

### Exploring Device Configurations
* Device running-configurations (routers, switches, firewalls) are located in `configs/terminal-2/`, `configs/terminal-3/`, and `configs/terminal-5/` for offline review and verification.

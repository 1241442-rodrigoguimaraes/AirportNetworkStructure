RCOMP 2025-2026 Project 1 – Sprint 3 planning
===========================================
### Sprint master: 1241442 ###

# 1. Sprint's backlog #

| Task  | Member responsible for the task | Task description                                                                                                                                                                                                                                                |
|-------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| T.3.1 | Henri Fontes                    | Update the `Terminal2.pkt` layer three Packet Tracer simulation from the previous sprint, to include the described features in this sprint for Terminal 2.                                                                                                      |
| T.3.2 | Miguel Ribeiro                  | Update the `Terminal3.pkt` layer three Packet Tracer simulation from the previous sprint, to include the described features in this sprint for Terminal 3. Final integration of each member’s Packet Tracer simulation into a single simulation: `campus.pkt`.  |
| T.3.3 | Rodrigo Guimarães               | Update the `Terminal5.pkt` layer three Packet Tracer simulation from the previous sprint, to include the described features in this sprint for Terminal 5.                                                                                                      |

# 2. Technical decisions and coordination #

## OSPF Area ID assignment ##

| OSPF Area ID |   Description   |     Networks Included      | Area Type |
|:------------:|:---------------:|:--------------------------:|:---------:| 
|      0       | Campus Backbone | 10.80.127.0/24 (VLAN 806)  | Backbone  |
|      2       |   Terminal 2    | T2 Subnets (VLANs 808-811) |  Regular  | 
|      3       |   Terminal 3    | T3 Subnets (VLANs 812-815) |  Regular  |
|      5       |   Terminal 5    | T5 Subnets (VLANs 816-819) |  Regular  |

## VoIP numbers and prefix schema ##

As a group decision, it was decided that the VoIP numbers would be four digits long, since it would be easier to manage this system and the configuration would be less prone to typing errors.

| Terminal | Prefix |
|:--------:|:------:|
|    2     |  2XXX  |
|    3     |  3XXX  | 
|    5     |  5XXX  |

|              Service              |    Range     |
|:---------------------------------:|:------------:|
|  Terminal 2 - Floor 1 (Arrivals)  | 2000 to 2166 |
| Terminal 2 - Floor 4 (Departures) | 2167 to 2332 | 
|    Terminal 2 - Administration    | 2333 to 2498 |
|     Terminal 2 - Informations     | 2499 to 2664 |
|   Terminal 2 - MEDBAY services    | 2665 to 2830 |
|  Terminal 2 - Security services   | 2831 to 2999 |
| Terminal 3 - Floor 1 (Departures) | 3000 to 3166 |
|  Terminal 3 - Floor 2 (Arrivals)  | 3167 to 3332 |
|    Terminal 3 - Administration    | 3333 to 3498 |
|     Terminal 3 - Informations     | 3499 to 3664 |
|   Terminal 3 - MEDBAY services    | 3665 to 3830 |
|  Terminal 3 - Security services   | 3831 to 3999 |
|  Terminal 5 - Floor 0 (Arrivals)  | 5000 to 5166 |
| Terminal 5 - Floor 2 (Departures) | 5167 to 5332 |
|    Terminal 5 - Administration    | 5333 to 5498 |
|     Terminal 5 - Informations     | 5499 to 5664 |
|   Terminal 5 - MEDBAY services    | 5665 to 5830 |
|  Terminal 5 - Security services   | 5831 to 5999 |

## DNS Domain Hierarchy ##

### Root Domain: `rcomp-25-26-2DJ-g4.pt`

* **Root Domain Authority:** Miguel Ribeiro

### Subdomains:
2. `t2.rcomp-25-26-2DJ-g4.pt`
3. `t3.rcomp-25-26-2DJ-g4.pt`
5. `t5.rcomp-25-26-2DJ-g4.pt`

| Terminal |        Subdomain         |    DNS Server Subdomain     | Web Server Subdomain         | DNS Server IP (NS) | Web Server IP (WWW) |
|:--------:|:------------------------:|:---------------------------:|------------------------------|:------------------:|:-------------------:|
|    T2    | t2.rcomp-25-26-2DJ-g4.pt | ns.t2.rcomp-25-26-2DJ-g4.pt | www.t2.rcomp-25-26-2DJ-g4.pt |     10.80.10.1     |     10.80.10.2      |
|    T3    | t3.rcomp-25-26-2DJ-g4.pt | ns.t3.rcomp-25-26-2DJ-g4.pt | www.t3.rcomp-25-26-2DJ-g4.pt |     10.80.50.2     |     10.80.50.4      |
|    T5    | t5.rcomp-25-26-2DJ-g4.pt | ns.t5.rcomp-25-26-2DJ-g4.pt | www.t5.rcomp-25-26-2DJ-g4.pt |    10.80.90.10     |     10.80.90.11     |

# 3. Subtasks assignment #

* 1241210 - Develop the network simulation for Terminal 3
* 1241442 - Develop the network simulation for Terminal 5
* 1241437 - Develop the network simulation for Terminal 2
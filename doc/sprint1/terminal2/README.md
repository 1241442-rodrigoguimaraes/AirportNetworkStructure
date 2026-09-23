RCOMP 2025-2026 Project 1 - Sprint 1 - Member 1241437 folder
===========================================

This is a document that clarifies and explains deeply **the cabling system plan for levels 1 and 4 of Terminal 2** at the given imaginary airport, implemented and designed by the **Sprint Master Henri Fontes**.

## Level 1 #

### Measurements

The measures were made using a set-square measuring tool after printing the "Sprint 1 - Description" document, and the result of the measurement was that **the 50 meters of the presented scale corresponded to
2,05 centimeters.** With that in mind, the following table shows the dimensions in meters converted from the measures in centimeters taken by the set-square measuring tool:

| Room | Dimensions (sidewall length $\times$ bottom wall length) | Total Area           |
|------|----------------------------------------------------------|----------------------|
| 1    | $(28,05 \times 14,63) \text{ m}$                         | $410,37 \text{ m}^2$ |
| 2    | $(21,95 \times 14,63) \text{ m}$                         | $321,13 \text{ m}^2$ |
| 3    | $(34,15 \times 14,63) \text{ m}$                         | $499,61 \text{ m}^2$ |
| 4    | $(39,02 \times 14,63) \text{ m}$                         | $570,86 \text{ m}^2$ |
| 5    | $(34,15 \times 14,63) \text{ m}$                         | $499,61 \text{ m}^2$ |
| 7    | $(28,05 \times 17,07) \text{ m}$                         | $478,81 \text{ m}^2$ |
| 8    | $(28,05 \times 17,07) \text{ m}$                         | $478,81 \text{ m}^2$ |

| Terminal Wall    | Length             |
|------------------|--------------------|
| Sidewalls        | $201,22 \text{ m}$ |
| Top/bottom walls | $202,44 \text{ m}$ |

#### Total Area of Level 1: $40.734,98 \text{ m}^2$

![Level 1 Measurements](doc/sprint1/1241437/images/M1.png)

### Network Outlets Deployment Schematic Plan

With the measures established, the though behind the design of the network outlets deployment plan is based on the rule of **two outlets for each $10 \text{ m}^2$**. So, the standard number of network outlets
for each room is presented in the following table:

| Room | Calculation demonstration                           | Standard number of network outlets |
|------|-----------------------------------------------------|------------------------------------|
| 1    | $(410,37 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 82$ outlets               |
| 2    | $(321,13 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 64$ outlets               |
| 3    | $(499,61 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 100$ outlets              |
| 4    | $(570,86 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 114$ outlets              |
| 5    | $(499,61 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 100$ outlets              |
| 7    | $(478,81 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 96$ outlets               |
| 8    | $(478,81 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 96$ outlets               |

The network outlets are distributed in the room so that within an approximate 3-meter radius there's an outlet available for use. In the case of room 1, the outlets are distributed as follows:

![Level 1 NODSP1](doc/sprint1/1241437/images/NODSP1.png)

The logic behind the shown distribution of outlets is: when the room is properly divided into squared spaces of 9 square meters each and the outlets are distributed as shown, then they are always distributed in
a 3-meter radius and also at the same time there'll always be a double outlet every 10 square meters, following this way both rules.

Now, the following schematic plan is for the sidewall on the right side and the wall on the bottom side of the terminal, in which both of them it's supposed to have **one network outlet every five meters**.

| Terminal Wall  | Calculation demonstration           | Total number of outlets |
|----------------|-------------------------------------|-------------------------|
| Right sidewall | $201,22 \text{ m} \div 5 \text{ m}$ | $\approx 40$ outlets    |
| Bottom wall    | $202,44 \text{ m} \div 5 \text{ m}$ | $\approx 41$ outlets    |

![Level 1 NODSPW1](doc/sprint1/1241437/images/NODSPW1.png)

### Access Points

Throughout the level, it was used 30 access points (APs) to spread Wi-Fi connection homogeneously, as the following figure shows:

![Level 1 APs](doc/sprint1/1241437/images/APs1.png)

### Cross-connects & Cable Pathways Deployment Schematic Plan

For the level 1, the cross-connects and cable pathways were deployed in the following way:

![Level 1 CCs & CPs](doc/sprint1/1241437/images/CCs&CPs1.png)

In total, there are 14 Horizontal Cross-Connects (HCCs) distributed at this level in order to attend the 733 ISO 8877 network outlets and the 30 APs. The HCs could not attend an area bigger than $1000 \text{ m}^2$, and the
maximum number of network outlets for each HC was 200. The HCs were connected to the IC by optical fiber cables, since this type of cable is appropriate for long distances (higher than 90 meters, maximum for cooper cable types). 
The HCs that didn't have a close floor cable passageway were connected to the IC by optical fiber cables that roam the ceiling. The ones that did were connected by optical fiber cables that roam the underground technical passways of the airport.
For the network outlets in the rooms, CAT7 cooper cables were used, connecting the HCs to the network outlets. This level of the terminal presents a MC (Main Cross-Connect), since it's the terminal that is in the center of the
airport campus, being the center of the Campus Backbone.

![Level 1 CPR](doc/sprint1/1241437/images/CPR1.png)

### Inventory for Level 1

| Distribution Point | Copper Ports | Copper Patch Panels (24p) | Copper U | Fiber Ports | Fiber Patch Panels (24p) | Fiber U | Total U | U with Oversizing ×4 | Recommended Rack |
|--------------------|-------------:|--------------------------:|---------:|------------:|-------------------------:|--------:|--------:|---------------------:|------------------|
| MC                 |            0 |                         0 |       0U |           3 |                        1 |      1U |      1U |                   4U | 1 enclosure 6U   |
| IC                 |            0 |                         0 |       0U |          28 |                        2 |      2U |      2U |                   8U | 1 enclosure 9U   |
| South-West HC      |           10 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| South HC           |           21 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| South-East HC      |           20 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| Center-East HC     |           20 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| North-East HC      |          110 |                         5 |       5U |           1 |                        1 |      1U |      6U |                  24U | 1 rack 42U       |
| North HC           |          168 |                         7 |       7U |           1 |                        1 |      1U |      8U |                  32U | 1 rack 42U       |
| North-West HC      |          200 |                         9 |       9U |           1 |                        1 |      1U |     10U |                  40U | 1 rack 42U       |
| Center-Up HC       |           96 |                         4 |       4U |           1 |                        1 |      1U |      5U |                  20U | 1 rack 42U       |
| Center-Down HC     |           96 |                         4 |       4U |           1 |                        1 |      1U |      5U |                  20U | 1 rack 42U       |
| West AP HC         |            6 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| Middle-West AP HC  |            6 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| Center AP HC       |            6 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| Middle-East AP HC  |            6 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| East AP HC         |            6 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |

## Level 4 #

For the fourth level of Terminal 2, the measures are the same as the ones presented in the first level, but the dimensions of the rooms are different. The scale adopted for the measurements is the same as the first level
(2.05 centimeters = 50 meters). The logic behind the positioning of the outlets and the distribution of the APs is the same as in the first level.

### Measurements

| Room | Dimensions (sidewall length $\times$ bottom wall length) | Total Area           |
|------|----------------------------------------------------------|----------------------|
| 1    | $(21,95 \times 12,20) \text{ m}$                         | $267,79 \text{ m}^2$ |
| 2    | $(21,95 \times 12,20) \text{ m}$                         | $267,79 \text{ m}^2$ |
| 3    | $(19,51 \times 12,20) \text{ m}$                         | $238,02 \text{ m}^2$ |
| 4    | $(19,51 \times 12,20) \text{ m}$                         | $238,02 \text{ m}^2$ |
| 5    | $(39,02 \times 14,63) \text{ m}$                         | $570,86 \text{ m}^2$ |
| 6    | $(34,15 \times 14,63) \text{ m}$                         | $499,61 \text{ m}^2$ |
| 7    | $(36,59 \times 14,63) \text{ m}$                         | $535,31 \text{ m}^2$ |
| 9    | $(19,51 \times 14,63) \text{ m}$                         | $285,43 \text{ m}^2$ |
| 10   | $(26,83 \times 14,63) \text{ m}$                         | $392,52 \text{ m}^2$ |
| 11   | $(19,51 \times 14,63) \text{ m}$                         | $285,43 \text{ m}^2$ |
| 12   | $(19,51 \times 14,63) \text{ m}$                         | $285,43 \text{ m}^2$ |
| 13   | $(19,51 \times 14,63) \text{ m}$                         | $285,43 \text{ m}^2$ |
| 14   | $(14,63 \times 14,63) \text{ m}$                         | $214,04 \text{ m}^2$ |

| Terminal Wall    | Length             |
|------------------|--------------------|
| Sidewalls        | $201,22 \text{ m}$ |
| Top/bottom walls | $202,44 \text{ m}$ |

#### Total Area of Level 4: $40.734,98 \text{ m}^2$

![Level 4 Measurements](doc/sprint1/1241437/images/M4.png)

### Network Outlets Deployment Schematic Plan

| Room | Calculation demonstration                           | Standard number of network outlets |
|------|-----------------------------------------------------|------------------------------------|
| 1    | $(267,79 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 54$ outlets               |
| 2    | $(267,79 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 54$ outlets               |
| 3    | $(238,02 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 48$ outlets               |
| 4    | $(238,02 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 48$ outlets               |
| 5    | $(570,86 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 114$ outlets              |
| 6    | $(499,61 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 100$ outlets              |
| 7    | $(535,31 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 108$ outlets              |
| 9    | $(285,43 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 58$ outlets               |
| 10   | $(392,52 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 80$ outlets               |
| 11   | $(285,43 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 58$ outlets               |
| 12   | $(285,43 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 58$ outlets               |
| 13   | $(285,43 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 58$ outlets               |
| 14   | $(214,04 \text{ m}^2 \times 2) \div 10 \text{ m}^2$ | $\approx 42$ outlets               |

![Level 4 NODSP4](doc/sprint1/1241437/images/NODSP4.png)

| Terminal Wall  | Calculation demonstration           | Total number of outlets |
|----------------|-------------------------------------|-------------------------|
| Right sidewall | $201,22 \text{ m} \div 5 \text{ m}$ | $\approx 40$ outlets    |
| Bottom wall    | $202,44 \text{ m} \div 5 \text{ m}$ | $\approx 41$ outlets    |

![Level 4 NODSPW4](doc/sprint1/1241437/images/NODSPW4.png)

### Access Points

![Level 4 APs](doc/sprint1/1241437/images/APs4.png)

### Cross-connects & Cable Pathways Deployment Schematic Plan

![Level 4 CCs & CPs](doc/sprint1/1241437/images/CCs&CPs4.png)

![Level 4 CPR](doc/sprint1/1241437/images/CPR4.png)

### Inventory for Level 4

| Distribution Point | Copper Ports | Copper Patch Panels (24p) | Copper U | Fiber Ports | Fiber Patch Panels (24p) | Fiber U | Total U | U with Oversizing ×4 | Recommended Rack |
|--------------------|-------------:|--------------------------:|---------:|------------:|-------------------------:|--------:|--------:|---------------------:|------------------|
| South-West HC      |           10 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| South HC           |           21 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| South-East HC      |           20 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| Center-East HC     |           20 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| North-East HC      |          200 |                         9 |       9U |           1 |                        1 |      1U |     10U |                  40U | 1 rack 42U       |
| North HC           |          200 |                         9 |       9U |           1 |                        1 |      1U |     10U |                  40U | 1 rack 42U       |
| North-West HC      |          136 |                         6 |       6U |           1 |                        1 |      1U |      7U |                  28U | 1 rack 42U       |
| Center-Up HC       |          174 |                         8 |       8U |           1 |                        1 |      1U |      9U |                  36U | 1 rack 42U       |
| Center-Down HC     |          100 |                         5 |       5U |           1 |                        1 |      1U |      6U |                  24U | 1 rack 42U       |
| Middle-West HC     |           80 |                         4 |       4U |           1 |                        1 |      1U |      5U |                  20U | 1 rack 42U       |
| West AP HC         |            6 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| Middle-West AP HC  |            6 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| Center AP HC       |            6 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| Middle-East AP HC  |            6 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |
| East AP HC         |            6 |                         1 |       1U |           1 |                        1 |      1U |      2U |                   8U | 1 enclosure 9U   |

### Inventory for Terminal 2

| Element                | Quantity |
|------------------------|---------:|
| Room outlets           |     1754 |
| APs                    |       60 |
| Total network points   |     1845 |
| Copper patch panels    |       88 |
| Fiber patch panels     |       32 |
| 42U racks              |       11 |
| Enclosures (6U/9U/12U) |       20 |

## Campus Backbone #

### Schematic Plan

The following figure shows the Campus Backbone schematic plan. The three terminals the group worked on are interconnected by the connection between the MC from the first level of Terminal 2 and the IC from the
first level of both Terminal 3 and 5. This connection is made by the use of optical fiber cables that roam the underground technical passways of the airport, since there's a long distance between the terminals
(higher than 90 meters, the maximum for cooper cables) and its cross-connect points.

![CB](doc/sprint1/1241437/images/CB.png)

### Total Inventory

| Element                | Quantity |
|------------------------|---------:|
| Room outlets           |     4814 |
| APs                    |      172 |
| Total network points   |     5041 |
| Copper patch panels    |      241 |
| Fiber patch panels     |       75 |
| 42U racks              |       26 |
| Enclosures (6U/9U/12U) |       45 |

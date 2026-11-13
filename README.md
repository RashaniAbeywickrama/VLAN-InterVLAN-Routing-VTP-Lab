# VLAN Configuration, Inter-VLAN Routing & VTP Lab

## Advanced Networking | Cisco Packet Tracer

---

## 📌 Project Overview

This project focuses on implementing VLAN segmentation, inter-VLAN routing and VLAN management using Cisco Packet Tracer.

The laboratory exercise is divided into two main sections:

1. VLAN Configuration and Inter-VLAN Routing
2. VLAN Trunking Protocol (VTP) Configuration

The first section demonstrates how VLANs logically separate network devices and how Router-on-a-Stick enables communication between different VLANs.

The second section demonstrates how VTP distributes VLAN information between switches using different VTP operating modes.

## 🎯 Objectives

- Configure and verify basic switch settings.
- Create and name multiple VLANs.
- Assign switch ports to appropriate VLANs.
- Configure 802.1Q trunk links.
- Implement Router-on-a-Stick inter-VLAN routing.
- Configure static routing between two network sites.
- Verify connectivity between VLANs and different branches.
- Configure VTP domains, passwords and operating modes.
- Understand VLAN propagation between VTP server, client and transparent switches.

# PART A – VLAN Configuration and Inter-VLAN Routing

## 🏗️ Network Architecture

The network consists of two sites, each containing multiple VLANs connected through routers.

### Site A

| VLAN | Department | Devices | Network |
|---|---|---|---|
| VLAN 10 | Management | Server1, Server2 | 192.168.10.0/24 |
| VLAN 20 | Sales | PC1, PC3 | 192.168.20.0/24 |
| VLAN 30 | HR | PC2, PC4 | 192.168.30.0/24 |

### Site B

| VLAN | Department | Network |
|---|---|---|
| VLAN 10 | Management | 192.168.110.0/24 |
| VLAN 20 | Sales | 192.168.120.0/24 |
| VLAN 30 | HR | 192.168.130.0/24 |

## 🌐 IP Addressing Plan

| Device / Network | IP Address |
|---|---|
| Site A VLAN 10 Gateway | 192.168.10.1 |
| Site A VLAN 20 Gateway | 192.168.20.1 |
| Site A VLAN 30 Gateway | 192.168.30.1 |
| Site A Router Link | 10.0.0.1/30 |
| Site B VLAN 10 Gateway | 192.168.110.1 |
| Site B VLAN 20 Gateway | 192.168.120.1 |
| Site B VLAN 30 Gateway | 192.168.130.1 |
| Site B Router Link | 10.0.0.2/30 |

## ⚙️ Implementation

### 1. VLAN Creation

Created VLANs 10, 20 and 30 on the switches at both sites.

Assigned appropriate VLAN names and configured end-device access ports.

### 2. VLAN Port Assignment

Configured switch access ports to connect PCs and servers to their respective VLANs.

This separated network traffic into logical broadcast domains.

### 3. 802.1Q Trunk Configuration

Configured trunk connections between switches and routers to carry traffic from multiple VLANs.

### 4. Router-on-a-Stick Configuration

Implemented inter-VLAN routing using router subinterfaces.

Each subinterface was configured with:
- An appropriate VLAN ID.
- 802.1Q encapsulation.
- An IP address acting as the VLAN default gateway.

### 5. Static Routing

Configured static routes between Router A and Router B to enable communication between the VLAN networks at both sites.

### 6. Connectivity Verification

Performed connectivity tests to verify:
- Communication between devices in the same VLAN across different sites.
- Communication between servers.
- Communication between servers and PCs.
- Routing between the two network sites.

## 🔍 Verification Commands

```bash
show vlan brief
show interfaces trunk
show ip interface brief
show ip route
show running-config
show ip arp
ping <destination-ip>
```

## 📸 Part A – Evidence

- VLAN creation and port assignment.
- Trunk link configuration.
- Router subinterface configuration.
- Static routing configuration.
- Successful inter-VLAN connectivity tests.
- Successful communication between Site A and Site B.

# PART B – VLAN Trunking Protocol (VTP)

## 📌 Overview

VLAN Trunking Protocol (VTP) is a Cisco proprietary protocol used to distribute VLAN configuration information between switches within the same VTP domain.

This section demonstrates VLAN management using three VTP operating modes.

## ⚙️ VTP Network Configuration

| Switch | VTP Mode | Responsibility |
|---|---|---|
| SW1 | Server | Creates and manages VLAN information |
| SW2 | Client | Learns VLAN information from the server |
| SW3 | Transparent | Maintains locally configured VLANs without participating in normal VLAN propagation |

**VTP Domain:** ccna-labs

## Implementation

### 1. VTP Domain Configuration

Configured the same VTP domain on all three switches.

### 2. VTP Password Configuration

Configured a common VTP authentication password for the lab switches.

### 3. VTP Operating Modes

- SW1 was configured as a VTP Server.
- SW2 was configured as a VTP Client.
- SW3 was configured as a VTP Transparent switch.

### 4. Trunk Configuration

Configured trunk links between switches to allow VLAN information to be exchanged.

### 5. VLAN Creation on SW1

Created the following VLANs on the VTP server:

| VLAN ID | VLAN Name |
|---|---|
| 10 | Sales |
| 20 | HR |

### 6. VLAN Propagation Verification

Verified that VLAN information created on SW1 was learned by SW2.

Checked that SW3 did not learn the server's VLAN information through normal VTP propagation.

### 7. Local VLAN Creation on SW3

Created VLAN 99 with the name Mgmt on the transparent switch.

Verified that this locally configured VLAN was not propagated to the other switches.

## 🔍 VTP Verification Commands

```bash
show vtp status
show vlan brief
show interfaces trunk
show running-config
```

## 📊 Key Concepts Demonstrated

| Concept | Description |
|---|---|
| VLAN | Logical network segmentation |
| Access Port | Connects end devices to a specific VLAN |
| Trunk Port | Carries traffic from multiple VLANs |
| 802.1Q | Standard VLAN tagging protocol |
| Router-on-a-Stick | Enables inter-VLAN routing using router subinterfaces |
| Static Routing | Manually configured routes between networks |
| VTP Server | Manages and advertises VLAN information |
| VTP Client | Learns VLAN information from the server |
| VTP Transparent | Maintains local VLAN configuration independently |

## 🧰 Technologies and Tools

- Cisco Packet Tracer
- Cisco IOS CLI
- VLAN Configuration
- 802.1Q Trunking
- Router-on-a-Stick
- Inter-VLAN Routing
- Static Routing
- VLAN Trunking Protocol (VTP)
- Network Troubleshooting

## 📸 Project Screenshots

The following evidence should be included:

1. Complete network topology.
2. VLAN creation and port assignment.
3. Trunk configuration.
4. Router subinterface configuration.
5. Static routing tables.
6. Successful inter-site connectivity tests.
7. VTP server configuration.
8. VTP client VLAN propagation.
9. VTP transparent mode verification.
10. VLAN 99 local configuration on SW3.

## ✅ Conclusion

This laboratory exercise provided practical experience in VLAN configuration, network segmentation, inter-VLAN routing and centralized VLAN management.

The Router-on-a-Stick implementation demonstrated how multiple VLANs can communicate through router subinterfaces using 802.1Q trunking.

Static routing enabled communication between separate network sites, while VTP demonstrated how VLAN information can be managed and distributed between switches using different operating modes.

Overall, the exercise strengthened practical understanding of switching, routing, network segmentation and VLAN administration.

---

*Advanced Networking Laboratory | BICT Undergraduate Portfolio*

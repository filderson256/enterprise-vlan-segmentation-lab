# Network Design Documentation

## 1. Introduction

This document describes the network architecture and design considerations for the implementation of an enterprise Local Area Network (LAN).

The proposed network is designed for an organization with four departments: Information Technology (IT), Finance, Human Resources (HR), and Administration.

The design uses Virtual Local Area Networks (VLANs) to logically separate departmental devices while allowing interdepartmental communication through a centralized Cisco router.

The network is simulated using Cisco Packet Tracer.

## 2. Network Design Objectives

The network is designed to achieve the following objectives:

- Implement logical network segmentation across organizational departments.
- Reduce unnecessary broadcast traffic between departmental networks.
- Enable communication between different VLANs through inter-VLAN routing.
- Provide centralized routing between departmental networks.
- Automate IP address allocation using DHCP.
- Establish a scalable foundation for future network expansion.
- Provide a foundation for implementing network access controls and security policies.

## 3. Network Architecture

The proposed architecture follows a hierarchical logical arrangement consisting of three main components:

### 3.1 Routing Layer

A Cisco 2911 router is responsible for routing traffic between the departmental VLANs.

Router-on-a-Stick is implemented using subinterfaces configured on the router's GigabitEthernet 0/0 interface.

Each subinterface is assigned a unique VLAN ID and IP address, which serves as the default gateway for its respective departmental network.

### 3.2 Switching Layer

A Cisco Catalyst 2960 Layer 2 switch provides connectivity for departmental computers.

The switch is configured with four VLANs. Access ports are assigned to their respective departmental VLANs.

The connection between the switch and router operates as an IEEE 802.1Q trunk, carrying traffic for all four VLANs.

### 3.3 End-User Layer

Eight computers represent departmental users.

Each department has two computers connected to dedicated switch access ports.

End-user computers obtain their IPv4 addresses automatically through DHCP.

## 4. Network Device Inventory

| Device | Model | Quantity | Function |
|---|---|---:|---|
| Router | Cisco 2911 | 1 | Inter-VLAN routing and DHCP |
| Switch | Cisco 2960 | 1 | Layer 2 switching and VLAN segmentation |
| Computers | End-user PCs | 8 | Departmental connectivity |

## 5. Physical and Logical Connectivity

The network uses the following connections:

| Source | Interface | Destination | Interface |
|---|---|---|---|
| R1 | G0/0 | SW1 | G0/1 |
| SW1 | Fa0/1 | IT-PC1 | Ethernet |
| SW1 | Fa0/2 | IT-PC2 | Ethernet |
| SW1 | Fa0/3 | Finance-PC1 | Ethernet |
| SW1 | Fa0/4 | Finance-PC2 | Ethernet |
| SW1 | Fa0/5 | HR-PC1 | Ethernet |
| SW1 | Fa0/6 | HR-PC2 | Ethernet |
| SW1 | Fa0/7 | Admin-PC1 | Ethernet |
| SW1 | Fa0/8 | Admin-PC2 | Ethernet |

## 6. VLAN Segmentation Strategy

Four VLANs are implemented to separate departmental network traffic.

| Department | VLAN ID | VLAN Name |
|---|---:|---|
| IT | 10 | IT |
| Finance | 20 | FINANCE |
| Human Resources | 30 | HR |
| Administration | 40 | ADMINISTRATION |

Each VLAN represents a separate logical broadcast domain.

Devices assigned to the same VLAN can communicate at Layer 2, subject to normal switching and host configuration requirements.

Communication between different VLANs requires Layer 3 routing.

## 7. Inter-VLAN Routing Design

Router-on-a-Stick is selected as the inter-VLAN routing method.

The router uses one physical interface connected to the switch through an 802.1Q trunk link.

Four logical subinterfaces are created:

| Router Subinterface | VLAN ID | Gateway IP |
|---|---:|---|
| G0/0.10 | 10 | 192.168.10.1 |
| G0/0.20 | 20 | 192.168.20.1 |
| G0/0.30 | 30 | 192.168.30.1 |
| G0/0.40 | 40 | 192.168.40.1 |

Each subinterface performs routing for its corresponding departmental network.

The router receives tagged Ethernet frames from the switch, processes them at Layer 3, and forwards packets to the appropriate destination VLAN.

## 8. DHCP Design

The Cisco 2911 router provides DHCP services for all four departmental networks.

Separate DHCP pools are configured for IT, Finance, HR, and Administration.

The first 20 addresses in each subnet are reserved for gateways and potential infrastructure devices.

DHCP automatically assigns end-user devices their IP addresses, subnet masks, and default gateways.

## 9. Traffic Flow

### 9.1 Communication Within the Same VLAN

When two computers belong to the same VLAN, traffic is switched locally by the Cisco 2960 switch.

The traffic does not require routing through the Cisco 2911 router.

### 9.2 Communication Between Different VLANs

When a computer communicates with a device in another VLAN:

1. The source computer identifies that the destination belongs to a different IP network.
2. It forwards the packet to its configured default gateway.
3. The switch forwards the tagged frame through the trunk link.
4. The router receives the frame through the corresponding subinterface.
5. The router examines its routing table and forwards the packet towards the destination VLAN.
6. The switch delivers the frame to the destination computer.

## 10. Design Considerations

The following considerations influenced the network design:

- **Scalability:** Additional departmental devices can be accommodated by assigning available switch ports to existing VLANs.
- **Manageability:** Departmental separation simplifies network administration.
- **Performance:** VLANs create separate broadcast domains.
- **Centralized routing:** Router-on-a-Stick provides a centralized point for inter-VLAN routing.
- **Address management:** DHCP reduces manual IP configuration.
- **Security:** VLAN separation provides logical segmentation but does not independently prevent inter-VLAN communication.

Additional security controls, such as extended Access Control Lists (ACLs), will be considered in a future project enhancement.

## 11. Current Design Limitations

The proposed design is intended for learning and demonstration purposes.

The following limitations are recognized:

- A single router represents a single point of failure.
- A single switch provides no switching redundancy.
- Router-on-a-Stick uses a shared physical trunk interface for inter-VLAN traffic.
- Inter-VLAN traffic is not yet restricted using ACLs.
- The design does not include redundant gateways or high availability.

These limitations can be addressed in more advanced enterprise network designs.

## 12. Conclusion

The proposed enterprise LAN design establishes a segmented network environment using Cisco routing and switching technologies.

The implementation provides practical experience in VLAN architecture, IEEE 802.1Q trunking, IPv4 addressing, Router-on-a-Stick, DHCP, and network connectivity.

The design also provides a foundation for future improvements involving network security, redundancy, and enterprise network management.

---

**Project:** Enterprise LAN Design and VLAN Segmentation

**Documentation:** Network Design

**Simulation Environment:** Cisco Packet Tracer

**Project Status:** In Progress

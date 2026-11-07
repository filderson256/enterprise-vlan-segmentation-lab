# Enterprise LAN Design and VLAN Segmentation

## 1. Project Overview

This project demonstrates the design and implementation of a segmented enterprise Local Area Network (LAN) using Cisco networking technologies.

The network consists of four departments: IT, Finance, Human Resources, and Administration. Each department is assigned a dedicated Virtual Local Area Network (VLAN) to improve network segmentation, manageability, and security.

Inter-VLAN communication is implemented using Cisco Router-on-a-Stick, allowing controlled communication between departmental networks through a centralized router.

## 2. Project Objectives

The main objectives of this project are:

- Design an enterprise LAN using Cisco networking devices.
- Implement VLANs to logically separate departmental networks.
- Configure access ports and IEEE 802.1Q trunking.
- Implement inter-VLAN routing using router subinterfaces.
- Configure DHCP for automatic IP address allocation.
- Verify communication between different VLANs.
- Perform basic network troubleshooting.

## 3. Network Topology

The simulated network consists of:

- 1 Cisco 2911 Router.
- 1 Cisco 2960 Layer 2 Switch.
- 8 End-user computers.
- 4 Departmental VLANs.

*The network topology diagram will be added here.*

## 4. Technologies and Tools

| Technology | Purpose |
|---|---|
| Cisco Packet Tracer | Network simulation |
| Cisco IOS | Router and switch configuration |
| VLANs | Departmental network segmentation |
| IEEE 802.1Q | VLAN trunking |
| Router-on-a-Stick | Inter-VLAN routing |
| DHCP | Automatic IP addressing |
| IPv4 | Network addressing |

## 5. VLAN and IP Addressing Scheme

| Department | VLAN ID | Network | Default Gateway |
|---|---:|---|---|
| IT | 10 | 192.168.10.0/24 | 192.168.10.1 |
| Finance | 20 | 192.168.20.0/24 | 192.168.20.1 |
| Human Resources | 30 | 192.168.30.0/24 | 192.168.30.1 |
| Administration | 40 | 192.168.40.0/24 | 192.168.40.1 |

## 6. Implementation

The implementation involves the following stages:

1. Physical network topology design.
2. Creation of departmental VLANs.
3. Assignment of switch access ports.
4. Configuration of the 802.1Q trunk link.
5. Configuration of router subinterfaces.
6. Implementation of inter-VLAN routing.
7. Configuration of DHCP services.
8. Network connectivity verification.

## 7. Network Verification

The following Cisco IOS commands are used to verify the implementation:

**Switch verification:**

- `show vlan brief`
- `show interfaces trunk`
- `show interfaces status`

**Router verification:**

- `show ip interface brief`
- `show ip route`
- `show ip dhcp binding`

**End-to-end connectivity:**

- Ping between computers within the same VLAN.
- Ping between computers in different VLANs.
- Verification of DHCP address allocation.

Actual command outputs and screenshots will be included in the verification directory.

## 8. Project Structure

```text
enterprise-vlan-segmentation-lab/
│
├── README.md
├── topology/
├── configurations/
├── documentation/
├── verification/
└── screenshots/
```

## 9. Expected Outcomes

Upon successful implementation, the network should demonstrate:

- Successful separation of departmental networks using VLANs.
- Correct operation of trunk links.
- Successful inter-VLAN routing.
- Automatic IP address allocation through DHCP.
- End-to-end connectivity between departmental computers.

## 10. Future Improvements

The project can be extended by implementing:

- Access Control Lists (ACLs) for departmental access restrictions.
- Port security.
- DHCP snooping.
- Spanning Tree Protocol (STP).
- EtherChannel.
- Network monitoring and troubleshooting.

## 11. Learning Outcomes

This project provides practical experience in enterprise LAN design, VLAN segmentation, IPv4 addressing, Cisco IOS configuration, inter-VLAN routing, DHCP implementation, and network troubleshooting.

---

**Project Category:** CCNA 200-301 Practical Networking Lab

**Status:** In Progress

**Environment:** Cisco Packet Tracer

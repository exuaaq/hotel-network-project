# Hotel Network Infrastructure Project

A complete enterprise-style hotel network designed and implemented in **Cisco Packet Tracer**. The project demonstrates modern networking concepts including **VLAN segmentation**, **dynamic routing with OSPF**, **DHCP-based IP address management**, and **secure remote administration using SSH**.

## Table of Contents

- [Overview](#overview)
- [Project Objectives](#project-objectives)
- [Network Architecture](#network-architecture)
- [VLAN and IP Addressing Plan](#vlan-and-ip-addressing-plan)
- [Routing Design](#routing-design)
- [Implemented Technologies](#implemented-technologies)
- [Security Features](#security-features)
- [Testing and Validation](#testing-and-validation)
- [How to Use](#how-to-use)
- [Learning Outcomes](#learning-outcomes)
- [Future Improvements](#future-improvements)
- [License](#license)

---

# Overview

This project presents the design and implementation of a complete network infrastructure for a multi-floor hotel environment using Cisco Packet Tracer.

The network was designed with a focus on:

- Scalability
- Security
- Network segmentation
- Automated configuration management
- Enterprise networking best practices

The infrastructure supports multiple hotel departments, each isolated within dedicated VLANs while maintaining secure inter-department communication through dynamic routing.

---

# Project Objectives

The primary objectives of this project were:

- Design a structured enterprise network topology
- Implement VLAN-based network segmentation
- Configure dynamic routing using OSPF
- Automate IP address assignment using DHCP
- Enable secure remote administration through SSH
- Demonstrate fault-tolerant routing between network segments
- Apply networking concepts commonly used in real-world enterprise environments

---

# Network Architecture

The network infrastructure spans **three hotel floors**, with each department assigned to its own VLAN and subnet.

The topology includes:

- Multiple Layer 2 switches
- Multiple routers interconnected via point-to-point links
- VLAN segmentation
- OSPF dynamic routing
- DHCP services
- SSH remote management
- Dedicated testing workstation for validation

### High-Level Design

```text
Floor 3
 ├── IT (VLAN 10)
 └── Admin (VLAN 20)

Floor 2
 ├── Sales (VLAN 30)
 ├── HR (VLAN 40)
 └── Finance (VLAN 50)

Floor 1
 ├── Logistics (VLAN 60)
 ├── Store (VLAN 70)
 └── Reception (VLAN 80)

             OSPF
        Router Interconnect
```

---

# VLAN and IP Addressing Plan

## Floor 1

| Department | VLAN | Network |
|------------|------|----------|
| Reception | 80 | 192.168.8.0/24 |
| Store | 70 | 192.168.7.0/24 |
| Logistics | 60 | 192.168.6.0/24 |

---

## Floor 2

| Department | VLAN | Network |
|------------|------|----------|
| Finance | 50 | 192.168.5.0/24 |
| HR | 40 | 192.168.4.0/24 |
| Sales | 30 | 192.168.3.0/24 |

---

## Floor 3

| Department | VLAN | Network |
|------------|------|----------|
| Admin | 20 | 192.168.2.0/24 |
| IT | 10 | 192.168.1.0/24 |

---

# Routing Design

## Inter-Router Point-to-Point Networks

| Link | Network |
|--------|---------|
| R1 ↔ R2 | 10.10.10.0/30 |
| R2 ↔ R3 | 10.10.10.4/30 |
| R3 ↔ R1 | 10.10.10.8/30 |

### Why /30 Networks?

The use of `/30` subnetting for router interconnections provides:

- Two usable host addresses
- Minimal IP address waste
- Clear point-to-point topology design
- Simplified troubleshooting and route management

---

## OSPF Dynamic Routing

Open Shortest Path First (OSPF) was implemented as the routing protocol for communication between VLANs and network segments.

Benefits include:

- Fast convergence
- Automatic route learning
- Scalable architecture
- Reduced administrative overhead
- Support for future network expansion

---

# Implemented Technologies

## VLAN Segmentation

- Department-based network isolation
- Reduced broadcast traffic
- Improved security boundaries
- Simplified network administration

---

## OSPF Routing

- Dynamic route exchange
- Automatic topology adaptation
- Efficient path selection
- Enterprise-standard routing protocol

---

## DHCP Services

Each router provides DHCP services for its associated VLANs.

Benefits:

- Automatic IP assignment
- Reduced configuration errors
- Simplified client onboarding
- Centralized address management

---

## SSH Remote Administration

SSH was configured on networking devices to provide secure remote management.

Features:

- Encrypted administrative sessions
- Secure device access
- Remote troubleshooting capability
- Improved operational security

---

# Security Features

The project incorporates multiple security-focused design decisions.

## Network Segmentation

- Department isolation through VLANs
- Controlled inter-network communication
- Reduced attack surface

## Secure Device Access

- SSH-enabled router management
- Encrypted administrative communication
- Prevention of insecure Telnet access

## Controlled Routing Environment

- Structured route advertisement using OSPF
- Organized subnet allocation
- Predictable traffic flow

---

# Testing and Validation

The network was validated through a series of functional tests.

## Connectivity Testing

- Inter-VLAN communication
- End-to-end network reachability
- Department-to-department connectivity

### Example

```bash
ping <destination-ip>
```

---

## OSPF Verification

Verification of dynamically learned routes:

```bash
show ip route ospf
```

---

## DHCP Verification

Verification of address allocation:

```bash
show ip dhcp binding
```

---

## SSH Verification

Remote administration testing:

```bash
ssh admin@<router-ip>
```

---

## Results

All major functionalities were successfully validated:

- VLAN communication
- OSPF route propagation
- DHCP address assignment
- SSH connectivity
- End-to-end network reachability

---

# How to Use

## 1. Open the Project

Launch the topology file in Cisco Packet Tracer.

---

## 2. Review Configurations

Inspect router and switch configurations through the CLI.

Example:

```bash
show running-config
```

---

## 3. Test Connectivity

Perform ping tests between devices located in different VLANs.

```bash
ping <destination-ip>
```

---

## 4. Verify Dynamic Routing

```bash
show ip route
show ip route ospf
```

---

## 5. Test SSH Access

```bash
ssh admin@<router-ip>
```

---

## 6. Extend the Topology

Additional VLANs, floors, routers, or services can be integrated to simulate larger enterprise deployments.

---

# Learning Outcomes

This project demonstrates practical experience with:

- Enterprise Network Design
- VLAN Configuration and Segmentation
- Subnetting and IP Address Planning
- Dynamic Routing with OSPF
- DHCP Configuration
- Secure Remote Administration (SSH)
- Cisco IOS CLI Configuration
- Network Troubleshooting
- Cisco Packet Tracer Simulation
- Layer 2 and Layer 3 Networking Concepts

---

# Future Improvements

Potential enhancements include:

- Access Control Lists (ACLs)
- Port Security
- Redundant Links with STP Optimization
- Network Address Translation (NAT)
- Wireless Network Integration
- Centralized Monitoring and Logging
- AAA Authentication (RADIUS/TACACS+)
- High Availability Routing Protocols (HSRP/VRRP)

---

# License

This project was developed for educational purposes and demonstrates enterprise networking concepts using Cisco Packet Tracer.

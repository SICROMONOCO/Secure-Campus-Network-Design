# Secure Campus Network Design

![Status](https://img.shields.io/badge/Status-Completed-success)
![Platform](https://img.shields.io/badge/Platform-Cisco%20Packet%20Tracer-blue)
![Architecture](https://img.shields.io/badge/Architecture-3--Layer%20Hierarchical-orange)

A comprehensive simulation of a scalable, secure, and converged enterprise network infrastructure. This project demonstrates a **3-Layer Hierarchical Architecture** (Core, Distribution, Access) implemented within Cisco Packet Tracer, featuring advanced security policies, VoIP integration, and high-availability protocols.

## Table of Contents
- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Architecture & Topology](#architecture--topology)
- [Technology Stack](#technology-stack)
- [Getting Started](#getting-started)
- [Network Credentials](#network-credentials)
- [Project Structure](#project-structure)
- [Future Roadmap](#future-roadmap)

## Project Overview
This repository contains the design artifacts, configuration scripts, and simulation files for a university campus network. The design addresses the needs of multiple departments (Administration, Faculty, Students) by implementing strict VLAN segmentation, centralized management services, and a converged Data/Voice network.

The deployment was executed in **5 Incremental Snapshots**, ensuring a stable progression from physical connectivity to advanced services.

## Key Features

### 🏛 Network Architecture
- **3-Layer Hierarchical Model:** Dedicated Core (High-speed switching), Distribution (Policy aggregation), and Access (User connectivity) layers.
- **Resiliency:** Link Aggregation via **LACP EtherChannels** (802.3ad) between all layers to prevent bottlenecks and provide redundancy.
- **Inter-VLAN Routing:** Centralized SVI-based routing performed by the Core Multilayer Switch.

### 🛡 Security Implementation
- **Recursive Management (Jump Host):** SSH access to Distribution and Access switches is restricted. Administrators must "hop" through the Core Switch (`200.200.255.254`) to reach downstream devices.
- **Data Plane Isolation:** Extended ACLs prevent inter-departmental traffic (e.g., Students cannot access Admin VLANs) while allowing access to shared servers.
- **Access Layer Hardening:** 
  - **Port Security:** Limits MAC addresses per port (1 PC + 1 Phone) with "Sticky" learning.
  - **DHCP Snooping:** Trusted boundaries configured to block Rogue DHCP servers.
- **AAA:** Centralized authentication via **RADIUS** with local fallback users.

### 📞 Converged Services (VoIP)
- **Cisco CME (Call Manager Express):** Deployed on an ISR Router to handle call signaling.
- **Voice VLANs:** Dedicated VLANs (Auxiliary VLANs) for IP Phones to ensure segmentation.
- **DHCP Option 150:** Automated TFTP server discovery for IP Phone provisioning.

## Architecture & Topology

### VLAN Segmentation Strategy
The network uses a Class C private addressing scheme (`200.200.x.x`), segmented by function and building.

## Technology Stack

| Category | Technologies / Protocols |
| :--- | :--- |
| **Switching** | VLANs (802.1Q), VTP v2, EtherChannel (LACP), STP |
| **Routing** | Inter-VLAN (SVI), Static Routing |
| **Security** | ACLs (Standard/Extended), Port Security, DHCP Snooping, AAA |
| **Services** | DHCP Relay, NTP, Syslog, TFTP, SSHv2 |
| **Voice** | SCCP, CME (Telephony Service), QoS (Trust CoS) |

## Getting Started

### Prerequisites
*   **Cisco Packet Tracer:** Version 8.0 or higher is required to open the `.pkt` simulation files.

### Installation & Usage
1.  **Clone the Repository:**
    ```bash
    git clone https://github.com/SICROMONOCO/Secure-Campus-Network-Design.git
    ```
2.  **Open the Simulation:**
    Navigate to the `simulation/` directory and open `Campus_Network_Final.pkt` in Cisco Packet Tracer.
3.  **Verify Connectivity:**
    *   Open the Command Prompt on any PC.
    *   Ping the Server Gateway: `ping 200.200.100.254`.
    *   Ping the Google DNS (Simulated): `ping 8.8.8.8`.

## Network Credentials

<details>
<summary><strong>🔐 Click to view Lab Credentials</strong></summary>

These credentials are used for the simulation lab environment.

| Device / Context | Username | Password | Secret |
| :--- | :--- | :--- | :--- |
| **Console / VTY** | - | `cisco` | - |
| **Enable Mode** | - | - | `class` |
| **Local Admin** | `mngr` | `mngr@2025` | - |
| **RADIUS Admin** | `admin` | `radius_pass` | `123456789A` (Shared Key) |
| **Radius Fallback** | `AdminLocal` | `Mngr@Reseau2025` | - |

</details>

## Project Structure

```text
Secure-Campus-Network-Design/
├── configs/                # Exported running-configs for all devices
│   ├── CORE_MLS.cfg
│   ├── ROUTER_CME.cfg
│   ├── DIST_SW_FP.cfg
│   └── ACCESS_SW_DEPT1.cfg
├── docs/                   # Documentation and Diagrams
│   ├── reports/            # Full Technical Report (PDF/MD)
│   └── topology/           # Network Diagrams (Logical/Physical)
├── simulation/             # Packet Tracer Source Files
│   ├── snapshots/          # Incremental backups (Snap 1-4)
│   └── Campus_Final.pkt    # Final Production Simulation
└── README.md
```

## Future Roadmap

The following improvements are recommended for the next iteration:

    Implementation of HSRP for First Hop Redundancy at the Core.
    Deployment of a WLC (Wireless LAN Controller) for centralized Wi-Fi management.
    Migration from ACLs to a Zone-Based Firewall or dedicated ASA.

---

Created by [SICROMONOCO] - 2026

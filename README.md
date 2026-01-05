
# Secure Campus Network Design PoC

![Status](https://img.shields.io/badge/Status-Completed-success)
![Platform](https://img.shields.io/badge/Platform-Cisco_Packet_Tracer-blue)
![Architecture](https://img.shields.io/badge/Architecture-3--Layer_Hierarchical-orange)

## Project Summary

This repository contains the Proof of Concept (PoC) for a scalable, secure, and convergent campus network infrastructure. Designed using the **Cisco 3-Layer Hierarchical Model** (Core, Distribution, Access), this simulation integrates advanced switching, routing, security, and VoIP telephony services.

The project demonstrates a production-ready environment capable of supporting administrative, educational, and guest traffic with strict logical isolation and high availability.

## Key Features

*   **Hierarchical Architecture:** Modular design separating Core (High-speed transport), Distribution (Policy/Routing), and Access (User connectivity) layers.
*   **High Availability:** Implementation of **EtherChannel (LACP)** for link redundancy and increased bandwidth between layers.
*   **Advanced Segmentation:** Granular **VLAN** strategy separating Data, Voice, Server, and Management traffic.
*   **Network Security:**
    *   **Layer 2 Security:** Port Security (MAC limiting), DHCP Snooping (Rogue server prevention), and ARP inspection readiness.
    *   **Layer 3 Security:** Recursive ACL design for "Jump Host" management and Inter-VLAN traffic restriction.
    *   **AAA:** Centralized authentication via RADIUS.
*   **Converged Services:** Integrated **VoIP** telephony using a Cisco ISR Router as a Call Manager Express (CME) with QoS prioritization.
*   **Infrastructure Management:** Standardized NTP clock synchronization, Syslog auditing, and SSH-only remote access.

## Technical Stack

| Component | Technology/Protocol | Details |
| :--- | :--- | :--- |
| **Simulation** | Cisco Packet Tracer | Version 8.2+ |
| **Switching** | 802.1Q, LACP, VTP | VLANs 100-200, Trunking |
| **Routing** | Inter-VLAN (SVI) | Router-on-a-Stick, Static Routing |
| **Security** | ACLs, Port Security | DHCP Snooping, SSHv2 |
| **Services** | DHCP, DNS, TFTP, NTP | RADIUS (AAA), Syslog |
| **Telephony** | SCCP, CME | Cisco Unified Communications Manager Express |

## Project Structure

```text
├── configs/
│   ├── core/
│   │   └── core_mls_running_config.txt
│   ├── distribution/
│   │   ├── sw1_sc_config.txt
│   │   ├── mls1_fp_config.txt
│   │   └── ...
│   ├── access/
│   │   └── access_switch_template.txt
│   └── router/
│       └── cme_router_config.txt
├── docs/
│   ├── logical_topology.png
│   ├── physical_cabling_matrix.md
│   └── full_project_report.pdf
├── simulation/
│   └── campus_network_final_snapshot_5.pkt
└── README.md

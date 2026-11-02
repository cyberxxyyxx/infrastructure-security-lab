# Network Infrastructure

## 1. Overview

The homelab network is designed to provide network segmentation, controlled access, traffic monitoring and isolated environments for infrastructure and cybersecurity testing.

The infrastructure combines:
- OPNsense firewall
- TP-Link TL-SG105E managed switch
- Proxmox VE virtual networking
- VLAN-based network segmentation
- Dedicated virtual machines for infrastructure, monitoring and security

## 2. Network Equipment

| Device | Model | Role |
|---|---|---|
| Firewall | Dell OptiPlex SFF | OPNsense firewall and routing |
| Managed Switch | TP-Link TL-SG105E | VLAN configuration |
| Virtualization Hosts | Lenovo ThinkCentre | Proxmox VE infrastructure |

## 3. Firewall & Routing

OPNsense is used as the central firewall and routing platform.

Main functionalities:
- Firewall rule configuration
- Network routing
- VLAN management
- Traffic filtering
- Network access control
- Connectivity troubleshooting

## 4. VLAN Architecture

The network is segmented into dedicated VLANs according to infrastructure roles.

| VLAN | Purpose | Devices / Services |
|---|---|---|
| VLAN 10 | Management | Proxmox SRV01, SRV02, SRV03, OPNsense Firewall and Managed Switch |
| VLAN 20 | Infrastructure | Domain Controllers and File Servers |
| VLAN 30 | Client Network | Windows Client |
| VLAN 40 | Monitoring | Prometheus / Grafana |
| VLAN 50 | Security | Elastic Security environment |
| VLAN 60 | Applications | Application services |
| VLAN 70 | Bastion | Controlled administrative access |
| VLAN 80 | Endpoint Network | 10Zig Zero Client |
| VLAN 90 | DMZ | Nginx Web Server |
| Dynamic | Security Testing | Kali Linux, assigned to the test VLAN |
| VLAN 100 | Malware Analysis | Isolated environment for malware analysis and security testing |
| VLAN 110 | Proxy | Squid Proxy Server for web traffic filtering, access control and logging |
| VLAN 110 | GOAD | Game Of Active Directory | 

## 5. Virtual Machine Network Mapping

| **VM** | **VLAN** | **IP Address** | **Role** |
|---|---:|---|---|
| DC-01 | 20 | 10.10.20.10 | Active Directory / DNS |
| FS-01 | 20 | 10.10.20.20 | File / Linux Services |
| DC-02 | 20 | 10.10.20.30 | Domain Controller |
| FS-02 | 20 | 10.10.20.40 | File Server |
| Windows Client | 30 | 10.10.30.10 | Client Workstation |
| MON-01 | 40 | 10.10.40.10 | Prometheus / Grafana |
| SEC-01 | 50 | 10.10.50.10 | Elastic Security / Security Monitoring |
| APP-01 | 60 | 10.10.60.10 | Application Services |
| BASTION-01 | 70 | 10.10.70.10 | Controlled Administration |
| 10Zig Zero Client | 80 | — | Endpoint |
| WEB-01 | 90 | 10.10.90.10 | Nginx Web Server / DMZ |
| MALWARE-01 | 100 | TBD | Malware Analysis / Isolated Testing Environment |
| PROXY-01 | 110 | TBD | Squid Proxy Server / Web Traffic Filtering |
| KALI-01 | Dynamic | Depends on test VLAN | Penetration Testing / Security Testing |

## 6. Virtual Networking

Proxmox VE provides virtual network connectivity through Linux bridges.

- vmbr0 – Virtual network bridge
- vmbr1 – Additional virtual network bridge
- VLAN tagging for virtual machines
- Connectivity between virtual machines and physical networks
- Network isolation through VLAN segmentation

## 7. Network Security & Testing

Practical activities performed in the homelab:

- VLAN configuration and troubleshooting
- Firewall rule testing
- Network segmentation validation
- Network scanning with Nmap
- Traffic analysis
- Testing communication between isolated networks
- Controlled administrative access through a Bastion host
- DMZ isolation for internet-facing services

## 8. Skills & Technologies

- OPNsense
- TP-Link Managed Switching
- VLAN Configuration
- Network Segmentation
- Firewall Management
- Routing
- Proxmox Virtual Networking
- Nmap
- Network Troubleshooting

---

*This documentation is continuously updated as the network infrastructure evolves.*

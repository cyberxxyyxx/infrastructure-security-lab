# OPNsense Firewall Configuration

## 1. Overview

OPNsense is the central firewall and routing platform in the homelab, providing network segmentation, traffic filtering and access control.

## 2. Hardware

| Specification | Details |
|---|---|
| Device | Dell OptiPlex SFF |
| Firewall | OPNsense |
| Role | Firewall and Router |

## 3. VLAN Configuration

| VLAN ID | Purpose | Description |
|---:|---|---|
| 10 | Management | Proxmox hosts, Firewall and Switch |
| 20 | Infrastructure | Active Directory and File Servers |
| 30 | Client Network | Windows Client |
| 40 | Monitoring | Prometheus / Grafana |
| 50 | Security | Elastic Security |
| 60 | Applications | Application Services |
| 70 | Bastion | Administrative Access |
| 80 | Endpoint | 10Zig Zero Client |
| 90 | DMZ | Nginx Web Server |
| 100 | Malware Analysis | Isolated Malware Testing |
| 110 | Proxy | Squid Proxy / Web Filtering |
| 120 | GOAD | Active Directory Security Testing |

## 4. Firewall Features

- Inter-VLAN Routing
- Firewall Rules
- Network Address Translation (NAT)
- DHCP and DNS
- Traffic Filtering
- Network Segmentation
- Access Control

## 5. Configuration Screenshots

### Firewall Dashboard!

### Firewall Interfaces

### Firewall Rules

## 6. Technologies

OPNsense, VLAN, IEEE 802.1Q, Routing, NAT, DHCP, DNS, Network Security.

---

*Homelab documentation – continuously updated.*

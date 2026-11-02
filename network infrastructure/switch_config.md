# Managed Switch Configuration

## 1. Overview

This document describes the managed switch configuration used in the homelab network infrastructure.

## 2. Hardware

| Specification | Details |
|---|---|
| Manufacturer | TP-Link |
| Model | TL-SG105E |
| Ports | 5 × Gigabit Ethernet |
| Management | Web-based interface |
| VLAN Support | IEEE 802.1Q |
| Features | Port-based VLAN, PVID, Port Mirroring |

## 3. VLAN Configuration

The switch is configured to support VLAN-based network segmentation.

Configured VLANs:

| VLAN ID | Purpose |
|---|---|
| 10 | Management |
| 20 | Infrastructure |
| 30 | Client Network |
| 40 | Monitoring |
| 50 | Security |
| 60 | Applications |
| 70 | Bastion |
| 80 | Endpoint |
| 90 | DMZ |
| 100 | Malware Analysis |
| 110 | Proxy |
| 120 | GOAD |
## 4. Switch Configuration Screenshots

### VLAN Configuration

![VLAN Configuration](images/vlan-configuration.png)

### Port Configuration

![Port Configuration](images/port-configuration.png)

### 802.1Q PVID Configuration

![PVID Configuration](images/pvid-configuration.png)

## 5. Configuration Objectives

- Separate network traffic using VLANs.
- Support communication between Proxmox hosts and virtual machines.
- Isolate infrastructure and security environments.
- Provide controlled connectivity through the OPNsense firewall.

## 6. Technologies

- TP-Link TL-SG105E
- IEEE 802.1Q
- VLAN Tagging
- PVID
- Network Segmentation
- OPNsense
- Proxmox VE

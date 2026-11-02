# Virtualization Infrastructure

## 1. Overview

The virtualization environment is built on Proxmox Virtual Environment (Proxmox VE), providing a flexible platform for hosting and managing virtual machines.

The infrastructure consists of three Lenovo ThinkCentre systems, configured to support different server workloads, network services and cybersecurity lab environments.

## 2. Proxmox VE Environment

Proxmox VE is used as the main virtualization platform for:

- Virtual machine deployment and management.
- Resource allocation and administration.
- Virtual networking and storage management.
- Linux and Windows server environments.
- Infrastructure and cybersecurity experimentation.

## 3. Hardware Nodes

The virtualization environment consists of three physical hosts:

| Node | Hardware | Processor | RAM |
|---|---|---|---|
| SRV01 | Lenovo M910q | Intel Core i5-9500T | 32 GB |
| SRV02 | Lenovo M920q | Intel Core i7-7700T | 32 GB |
| SRV03 | Lenovo M710q | Intel Core i5-6500T | 32 GB |

**Total hardware resources:**
- 3 physical hosts
- 14 physical CPU cores
- 18 logical CPU threads
- 96 GB RAM

## 4. Virtual Machine Management

The environment hosts virtual machines running different operating systems and infrastructure services.

### Windows Environment
- Windows Server
- Active Directory
- DNS and DHCP
- Windows Client

### Linux Environment
- Ubuntu Server
- Linux infrastructure services
- Bastion host
- Web server

### Cybersecurity Environment
- Kali Linux
- Elastic Security
- Security monitoring and testing tools

## 5. Storage Architecture

The physical hosts use a combination of NVMe, SSD and HDD storage.

Storage is used for:
- Proxmox VE installation.
- Virtual machine disks.
- Operating system images.
- Application and lab data.

## 6. Virtual Networking

Proxmox virtual networking provides connectivity between virtual machines and the physical network infrastructure.

The environment uses:
- Linux bridges (`vmbr0`, `vmbr1`).
- VLAN tagging.
- Virtual network interfaces.
- Integration with OPNsense firewall.
- Network segmentation.

## 7. Administration & Troubleshooting

Practical administration activities include:

- Virtual machine deployment and configuration.
- CPU and memory resource allocation.
- Storage management.
- Linux bridge configuration.
- VLAN connectivity troubleshooting.
- Network connectivity testing.
- Virtual machine administration.

## 8. Skills & Technologies

- Proxmox VE
- Virtualization
- Linux Administration
- Windows Server
- Virtual Networking
- VLAN Configuration
- Storage Management
- Infrastructure Troubleshooting

---

*This documentation is continuously updated as the virtualization environment evolves.*

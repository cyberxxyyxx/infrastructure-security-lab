# Cybersecurity Lab: Elastic Security SIEM – RDP Failed Login Detection

## Windows Authentication Monitoring, Failed RDP Logons & SIEM Alerts

**Project Type:** Cybersecurity / SIEM / Security Monitoring / Threat Detection

## Project Video

[Watch the project demonstration on YouTube](https://www.youtube.com/watch?v=cfCilGGANMQ&t=188s)

---

## 1. Project Overview

This project demonstrates a Windows authentication monitoring and security investigation environment using Kali Linux, Nmap, Windows Security Event Logs, and Elastic Security.

The main objective is to identify exposed Remote Desktop Protocol (RDP) services, perform controlled failed authentication attempts against a Windows endpoint, and investigate the generated security events through Elastic Security.

Nmap is used for network and service discovery to identify exposed ports and running services, including RDP on TCP port `3389`.

Controlled RDP authentication attempts are then performed against the target Windows system, generating failed logon events recorded in the Windows Security Event Log under Event ID `4625`.

Elastic Agent collects and forwards the Windows Security Events to the Elastic Stack, allowing centralized investigation of authentication activity through Kibana Discover and Elastic Security.

The project demonstrates how SIEM solutions can provide visibility into failed authentication activity, support security event investigation, and generate alerts based on configured detection rules.

## 2. Lab Architecture

The environment consists of multiple virtual machines hosted on Proxmox VE and connected through a segmented network infrastructure.

### Main Components

| **Component** | **Technology** | **Purpose** |
|---|---|---|
| Security Testing | Kali Linux | Perform network reconnaissance and controlled RDP authentication testing |
| Network Scanner | Nmap | Identify exposed ports and running services |
| Authentication Testing | Remote Desktop Protocol (RDP) | Generate controlled failed authentication attempts |
| Target | Windows Endpoint | Generate Windows security and authentication events |
| Event Monitoring | Windows Security Event Logs | Record failed logon events (Event ID 4625) |
| Endpoint Monitoring | Elastic Agent | Collect and forward Windows Security Events |
| SIEM | Elastic Security | Security monitoring, detection rules, and alert investigation |
| Data Storage | Elasticsearch | Store and index collected security events |
| Visualization | Kibana | Search, analyze, and investigate authentication events |
| Virtualization | Proxmox VE | Host the lab infrastructure |

### Architecture Overview

The architecture illustrates how authentication events are generated on the Windows endpoint, collected by Elastic Agent, and forwarded to the Elastic Stack infrastructure.

Kali Linux performs network reconnaissance against the target Windows system and identifies the exposed RDP service on TCP port `3389`.

Following service discovery, controlled failed RDP authentication attempts generate Windows Security Event ID `4625`.

Elastic Agent collects the relevant security events and forwards them to Elasticsearch for centralized storage and indexing.

Kibana Discover is used to investigate authentication activity, while Elastic Security provides detection rule configuration and SIEM alert investigation.

### Traffic & Data Flow

1. Kali Linux performs network reconnaissance against the Windows endpoint.
2. Nmap identifies exposed services, including RDP on TCP port `3389`.
3. Kali Linux initiates controlled RDP authentication attempts.
4. Windows records failed authentication attempts in the Security Event Log.
5. Windows generates Event ID `4625`.
6. Elastic Agent collects the relevant Windows Security Events.
7. Events are forwarded to Elasticsearch.
8. Elasticsearch stores and indexes the collected security telemetry.
9. Kibana Discover is used to search and investigate failed authentication events.
10. Elastic Security evaluates the configured detection rule and generates alerts when its conditions are met.

## 3. Implementation

- Identify the Windows endpoint IP address used as the RDP testing target.
- Prepare the Kali Linux testing environment.
- Perform network and service discovery using Nmap.
- Identify exposed services, including Remote Desktop Protocol (RDP) on TCP port `3389`.
- Perform multiple controlled RDP authentication attempts using different passwords.
- Generate Windows failed logon events (Event ID `4625`).
- Collect Windows Security Events using Elastic Agent.
- Investigate failed authentication events in Elastic Security using Kibana Discover and KQL.
- Configure a custom detection rule to monitor failed Windows authentication events.
- Review and investigate the generated SIEM alerts.

## 4. Security Monitoring

The lab focuses on monitoring and investigating:

- Network reconnaissance activity.
- Nmap service discovery.
- Exposed Remote Desktop Protocol services.
- RDP authentication attempts.
- Windows failed logon events.
- Windows Security Event ID `4625`.
- Source IP addresses.
- Targeted user accounts.
- Authentication timestamps.
- Windows logon types and failure information.
- Windows Security Events collected in Elastic Security.
- Custom detection rules and SIEM alerts.

This workflow demonstrates how endpoint authentication events can be collected, analyzed, and correlated with controlled testing activity to support security monitoring and investigation.

## 5. Technologies & Tools

- Kali Linux
- Nmap
- Remote Desktop Protocol (RDP)
- Windows Server / Windows Endpoint
- Windows Security Event Logs
- Windows Event ID 4625
- Elastic Stack
- Elasticsearch
- Kibana
- Elastic Security
- Elastic Agent
- Fleet Server
- KQL (Kibana Query Language)
- Proxmox VE
- Virtualized Cybersecurity Lab

## 6. Proof of Evidence

Screenshots documenting target identification, Nmap service discovery, RDP authentication attempts, Windows failed logon events, and Elastic Security investigation are included in the `images/` directory.

Detailed configuration steps, implementation screenshots, testing results, and technical evidence are documented in `TECHNICAL_DOCUMENTATION.md`.

## 7. Skills Demonstrated

- Network Reconnaissance
- Service Discovery and Enumeration
- Nmap Scanning
- RDP Authentication Testing
- Windows Security Event Analysis
- Failed Logon Monitoring
- Event ID 4625 Investigation
- Elastic Agent Integration
- SIEM Log Collection and Investigation
- KQL Query Development
- Custom Detection Rule Configuration
- SIEM Alert Investigation
- Security Event Analysis
- Threat Detection Fundamentals
- Cybersecurity Lab Administration

---

*Educational cybersecurity project developed and tested in a controlled homelab environment.*

# Cybersecurity Lab: Elastic Security SIEM

## Security Event Monitoring, Failed Login Detection & SIEM Alerts

**Project Type:** Cybersecurity / SIEM / Security Monitoring / Threat Detection

**Project Video:** [Watch the project demonstration on YouTube](https://www.youtube.com/watch?v=cfCilGGANMQ&t=188s)

---

## 1. Project Overview

This project demonstrates the implementation and use of Elastic Security SIEM in a virtualized cybersecurity lab environment.

The objective is to collect, monitor, analyze, and investigate security events generated across monitored systems.

The project explores how Elastic Security can be used to identify suspicious authentication activity, detect repeated failed login attempts, configure custom detection rules, and generate SIEM alerts.

As part of the practical demonstration, controlled failed RDP authentication attempts are generated against a Windows endpoint. The resulting security events are collected and analyzed in Elastic Security.

The project highlights the role of SIEM solutions in providing centralized security visibility, identifying potentially suspicious activity, and supporting security investigations.

## 2. Lab Architecture

The environment consists of multiple virtual machines hosted on Proxmox VE and connected through a segmented network infrastructure.

### Main Components

| Component | Description |
|---|---|
| Elastic Security | SIEM platform for security monitoring and threat detection |
| Elasticsearch | Stores and indexes security events |
| Kibana | Interface for event analysis, dashboards, and alerts |
| Fleet Server | Centralized Elastic Agent management |
| Elastic Agent | Collects and forwards endpoint telemetry |
| Windows Endpoint | Generates Windows security and authentication events |
| Kali Linux | Used to simulate controlled authentication attempts |
| Proxmox VE | Virtualization platform hosting the lab |

### Architecture Overview

The architecture illustrates how authentication events are generated on the Windows endpoint, collected by Elastic Agent, and forwarded to the Elastic Stack infrastructure.

Elasticsearch stores and indexes the collected events, while Kibana and Elastic Security provide the tools for event analysis, detection rule configuration, alert generation, and investigation.

### Traffic & Data Flow

1. Kali Linux initiates controlled authentication attempts against the Windows endpoint.
2. The Windows endpoint generates security events.
3. Elastic Agent collects the relevant Windows Security Events.
4. Events are forwarded to Elasticsearch.
5. Elasticsearch indexes and stores the collected telemetry.
6. Kibana Discover is used to search and analyze authentication events.
7. Elastic Security evaluates configured detection rules.
8. SIEM alerts are generated and investigated.

## 3. Implementation

### Step 1 – Lab Environment Preparation

Prepare the virtual machines and network infrastructure required for the SIEM environment.

Verify connectivity between the Windows endpoint, Kali Linux, and Elastic Stack infrastructure.

### Step 2 – Elastic Stack Configuration

Deploy and configure the required Elastic components:

- Elasticsearch
- Kibana
- Fleet Server
- Elastic Security

Verify that the services are operational and accessible within the lab network.

### Step 3 – Windows Endpoint Integration

Install and enroll Elastic Agent on the Windows endpoint through Fleet.

Configure the required integration to collect Windows Security Events.

Verify that the endpoint is connected and that security events are being received by Elastic.

### Step 4 – Authentication Event Generation

Perform controlled failed RDP login attempts against the Windows endpoint.

Use different passwords to generate multiple failed authentication events.

Windows records these attempts in the Security Event Log, including Event ID `4625`, which represents a failed logon.

### Step 5 – Security Event Analysis

Use Kibana Discover to search and analyze the collected Windows authentication events.

Investigate relevant fields, including:

- `host.name`
- `source.ip`
- `user.name`
- `event.code`
- `event.outcome`
- `@timestamp`

Use KQL (Kibana Query Language) to filter and investigate failed authentication events.

### Step 6 – Detection Rules & SIEM Alerts

Configure a custom detection rule in Elastic Security to identify repeated failed authentication attempts.

Review the generated SIEM alerts and investigate the associated event information.

Analyze the source IP address, targeted username, event timestamps, and number of failed attempts.

## 4. Security Monitoring & Investigation

The project demonstrates how Elastic Security can support security monitoring and investigation by providing centralized visibility into endpoint authentication activity.

The practical scenario focuses on:

- Monitoring Windows authentication events
- Identifying failed login attempts
- Investigating repeated authentication failures
- Analyzing Event ID `4625`
- Identifying source IP addresses
- Monitoring targeted user accounts
- Configuring SIEM detection rules
- Generating and investigating security alerts

This workflow demonstrates how raw security events can be transformed into actionable SIEM alerts that support security investigations.

## 5. Technologies & Tools

- Elastic Security
- Elasticsearch
- Kibana
- Fleet Server
- Elastic Agent
- KQL (Kibana Query Language)
- Windows Security Event Logs
- Windows Event ID 4625
- Remote Desktop Protocol (RDP)
- Kali Linux
- Proxmox VE
- Virtualized Cybersecurity Lab

## 6. Proof of Evidence

Screenshots and supporting materials demonstrate the lab architecture, endpoint integration, authentication event generation, event collection, detection rule configuration, and SIEM alerts.

See the `images/` directory for visual evidence.

## 7. Skills Demonstrated

- SIEM deployment and configuration
- Elastic Stack administration
- Endpoint integration and monitoring
- Windows Security Event Analysis
- Authentication monitoring
- KQL query development
- Custom detection rule configuration
- SIEM alert generation and investigation
- Security event analysis
- Threat detection fundamentals
- Cybersecurity lab administration

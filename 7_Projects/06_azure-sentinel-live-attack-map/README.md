# Cybersecurity Lab: Microsoft Azure Sentinel – Live Map of RDP Attacks

## Cloud SIEM, Failed Login Monitoring & Geolocation Visualization

**Project Type:** Cybersecurity / Cloud Security / SIEM / Threat Detection

## Project Video

[![Watch the project demonstration](https://img.youtube.com/vi/Y0DIDUPPOm4/maxresdefault.jpg)](https://www.youtube.com/watch?v=Y0DIDUPPOm4&t=179s)

## Project Reference

Inspired by **[Josh Madakor](https://www.youtube.com/@JoshMadakor)**.

[Original Tutorial – Live Map of RDP Attacks](https://www.youtube.com/watch?v=RoZeVbbZ0o0&t=1627s)

---

## 1. Project Overview

This project demonstrates a cloud-based SIEM environment using Microsoft Azure and Microsoft Sentinel.

A Windows virtual machine is monitored for failed RDP authentication attempts (Event ID `4625`). PowerShell extracts the events, enriches source IP addresses with geolocation data, and sends the processed information to Azure Log Analytics.

Microsoft Sentinel uses the collected data to visualize authentication activity on a geographic map.

## 2. Lab Architecture

### Main Components

| **Component** | **Technology** | **Purpose** |
|---|---|---|
| Cloud Platform | Microsoft Azure | Cloud infrastructure |
| Target | Windows 10 Pro VM | Generates security events |
| Event Monitoring | Windows Event Viewer | Records failed logons |
| Data Extraction | PowerShell | Extracts Event ID 4625 |
| Geolocation | IPGeolocation.io API | Resolves IP locations |
| SIEM Storage | Azure Log Analytics | Stores collected data |
| SIEM | Microsoft Sentinel | Security monitoring |
| Visualization | Sentinel Workbooks | Geographic attack visualization |

### Architecture Overview

Windows Security Events are extracted using PowerShell and enriched with geographic information through IPGeolocation.io.

The processed data is uploaded to Azure Log Analytics and visualized through a custom Microsoft Sentinel Workbook.

### Traffic & Data Flow

1. External systems initiate RDP authentication attempts.
2. Windows generates failed logon events (4625).
3. PowerShell extracts the security events.
4. Source IP addresses are enriched with geolocation data.
5. Processed events are exported into JSON.
6. Data is uploaded to Azure Log Analytics.
7. Microsoft Sentinel displays the results on a geographic map.

## 3. Implementation

- Deploy a Windows 10 Pro virtual machine in Azure.
- Configure Azure Log Analytics Workspace.
- Connect Microsoft Sentinel to the workspace.
- Generate controlled failed RDP authentication attempts.
- Identify Event ID `4625` in Windows Event Viewer.
- Configure PowerShell event extraction.
- Integrate IPGeolocation.io API.
- Export processed events into JSON.
- Configure custom log ingestion.
- Create KQL queries and a Sentinel Workbook.
- Visualize authentication attempts on a geographic map.

## 4. Security Monitoring

The project focuses on:

- Failed RDP authentication attempts.
- Windows Event ID `4625`.
- Source IP address identification.
- IP geolocation enrichment.
- Centralized security event collection.
- KQL-based event analysis.
- Geographic visualization of suspicious authentication activity.

## 5. Technologies & Tools

- Microsoft Azure
- Microsoft Sentinel
- Azure Log Analytics
- Microsoft Defender for Cloud
- Windows 10 Pro
- PowerShell
- Windows Event ID 4625
- IPGeolocation.io API
- JSON
- KQL
- Sentinel Workbooks
- Remote Desktop Protocol (RDP)

## 6. Proof of Evidence

The project video demonstrates the complete implementation, including Azure deployment, event extraction, geolocation enrichment, log ingestion, and the final interactive attack map.

## 7. Skills Demonstrated

- Cloud SIEM Implementation
- Microsoft Azure Administration
- Microsoft Sentinel
- Windows Security Event Analysis
- PowerShell Scripting
- API Integration
- IP Geolocation
- JSON Data Processing
- KQL Query Development
- SIEM Data Visualization
- Cloud Security Monitoring

---

**Security Note:** The Windows VM was configured with permissive network access for educational testing. Such configurations should not be used on production systems.

*Educational cybersecurity project developed in a controlled cloud lab environment.*

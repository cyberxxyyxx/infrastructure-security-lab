# Cybersecurity Lab: Elastic Stack & Squid Proxy
## Web Security Monitoring & Domain Filtering

**Project Type:** Cybersecurity / SIEM / Network Security

## Project Video

[Watch the project demonstration on YouTube](https://www.youtube.com/watch?v=fr7El30sC50&t=131s)

---

## 1. Project Overview

This project demonstrates a web security monitoring environment using Squid Proxy and Elastic Stack.

The main objective is to control web access through a periodically updated list of restricted domains, collect proxy logs and monitor blocked and allowed web requests using Elastic Security.

## 2. Lab Architecture

| Component | Technology | Purpose |
|---|---|---|
| Proxy Server | Squid | Web traffic filtering and access control |
| Domain Blocklist | Custom domain list | Maintain restricted domains |
| SIEM | Elastic Security | Security monitoring and log analysis |
| Log Collection | Filebeat | Forward Squid logs to Elastic |
| Client | Windows 10 | Generate web traffic |
| Firewall | OPNsense | Network segmentation and traffic control |

## 3. Implementation

- Squid Proxy installation and configuration
- Custom restricted domain list
- Periodic domain blocklist updates
- Access control using Squid ACL rules
- Blocking access to restricted domains
- Logging blocked and allowed requests
- Filebeat integration with Elastic
- Security event analysis in Kibana

## 4. Security Monitoring

The lab monitors:

- Blocked domain access attempts
- Allowed web requests
- HTTP response codes
- Client IP addresses
- Repeated attempts to access restricted domains
- Proxy traffic patterns

## 5. Technologies & Tools

- Squid Proxy
- Elastic Stack
- Elastic Security
- Filebeat
- Ubuntu Server
- Windows 10
- OPNsense
- Proxmox VE

## 6. Proof of Evidence

Screenshots documenting proxy configuration, domain filtering, blocklist updates and Elastic monitoring are available in the `evidence/` directory.

## 7. Skills Demonstrated

- Linux System Administration
- Squid Proxy Configuration
- Domain Filtering and Access Control
- ACL Management
- Log Management
- SIEM Integration
- Security Event Analysis
- Network Security

---

*Educational cybersecurity project developed and tested in a controlled homelab environment.*

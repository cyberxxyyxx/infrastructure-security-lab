# Cybersecurity Lab: Elastic Security – Web Reconnaissance & Directory Enumeration
## Web Server Discovery, Directory Enumeration & Security Monitoring

**Project Type:** Cybersecurity / SIEM / Web Security / Threat Detection

## Project Video

[Watch the project demonstration on YouTube.](VIDEO_URL)

## 1. Project Overview

This project demonstrates a web reconnaissance and security monitoring environment using Kali Linux, Nmap, Gobuster, Nginx, and Elastic Security.

The main objective is to identify exposed web services, perform directory enumeration against an Ubuntu Nginx Web Server, and investigate the generated HTTP requests through Elastic Security.

Nmap is used for network and service discovery, while Gobuster performs web directory enumeration to identify accessible paths and resources.

Nginx access logs are collected and forwarded to Elastic Security, allowing investigation of HTTP requests generated during the reconnaissance activity.

## 2. Lab Architecture

| **Component** | **Technology** | **Purpose** |
|---|---|---|
| Security Testing | Kali Linux | Perform network reconnaissance and web enumeration |
| Network Scanner | Nmap | Identify exposed ports and running services |
| Directory Enumeration | Gobuster | Discover accessible web directories and paths |
| Web Server | Ubuntu Server / Nginx | Host the web application and generate HTTP access logs |
| SIEM | Elastic Security | Centralized log collection and security event investigation |
| Log Collection | Nginx Access Logs | Record incoming HTTP requests |
| Source Host | Kali Linux | Simulated attacker performing reconnaissance |
| Target | WEB-01 | Ubuntu Linux Nginx Web Server |
| Virtualization | Proxmox VE | Host the lab infrastructure |

## 3. Implementation

- Prepare the Kali Linux testing environment.
- Configure the Ubuntu Linux Web Server with Nginx.
- Perform network and service discovery using Nmap.
- Identify exposed web services and open ports.
- Use Gobuster to enumerate web directories and accessible paths.
- Generate HTTP requests against the Nginx Web Server.
- Collect Nginx access logs.
- Forward web server logs to Elastic Security.
- Investigate HTTP activity generated during reconnaissance.

## 4. Security Monitoring

The lab focuses on monitoring and investigating:

- Network reconnaissance activity.
- Nmap service discovery.
- Web directory enumeration using Gobuster.
- HTTP requests targeting the Nginx Web Server.
- Requested URLs and directory paths.
- HTTP response status codes.
- Source IP addresses.
- Suspicious web access patterns.
- Nginx access events collected in Elastic Security.

## 5. Technologies & Tools

- Kali Linux
- Nmap
- Gobuster
- Ubuntu Server
- Nginx Web Server
- Elastic Stack
- Elastic Security
- Kibana
- HTTP Access Logs
- Proxmox VE

## 6. Proof of Evidence

Screenshots documenting the network scan, web directory enumeration, Nginx access logs, and Elastic Security event investigation are included in the `images/` directory.

Detailed configuration steps, implementation screenshots, testing results, and technical evidence are documented in `TECHNICAL_DOCUMENTATION.md`.

## 7. Skills Demonstrated

- Network Reconnaissance
- Service Discovery and Enumeration
- Nmap Scanning
- Web Directory Enumeration
- Gobuster Usage
- HTTP Traffic Analysis
- Nginx Access Log Monitoring
- SIEM Log Collection and Investigation
- Elastic Security
- Security Event Analysis
- Web Attack Surface Assessment

---

*Educational cybersecurity project developed and tested in a controlled homelab environment.*

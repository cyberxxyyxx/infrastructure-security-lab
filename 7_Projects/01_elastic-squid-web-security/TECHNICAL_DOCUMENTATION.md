# Technical Documentation

## Squid Proxy & Elastic Security Integration

## 1. Lab Environment

The lab consists of three main systems operating in separate VLANs.

| Hostname | IP Address | Role | VLAN |
|---|---|---|---|
| CLIENT-02 | 10.10.30.20 | Windows Client | VLAN 30 |
| PROXY-01 | 10.10.110.10 | Ubuntu Server / Squid Proxy | VLAN 110 |
| SEC-01 | 10.10.50.10 | Elastic Security | VLAN 50 |

## 2. Architecture

The Windows client uses Squid Proxy to filter web traffic. Squid access logs are collected by Filebeat and forwarded to Elastic Security for monitoring and analysis.

![Network Architecture](https://raw.githubusercontent.com/cyberxxyyxx/infrastructure-security-lab/main/7_Projects/01_elastic-squid-web-security/images/00-diagram.png)

### Traffic Flow

1. CLIENT-02 sends web requests through Squid Proxy.
2. Squid checks access control and domain filtering rules.
3. Allowed requests are forwarded to the Internet.
4. Squid generates access logs.
5. Filebeat collects and forwards the logs to Elastic Security.
6. Elastic Security provides visibility into web traffic and blocked requests.

## 3. Implementation Steps

### Step 1 – Squid Proxy Configuration

- Connect to the Ubuntu Proxy Server.

![Proxy Server Access](https://raw.githubusercontent.com/cyberxxyyxx/infrastructure-security-lab/main/7_Projects/01_elastic-squid-web-security/images/01-proxy-server-access.png)

- Locate the Squid configuration file (`/etc/squid/squid.conf`).
- Open the file using Nano.
```bash
sudo nano /etc/squid/squid.conf
```


![Squid Configuration](https://raw.githubusercontent.com/cyberxxyyxx/infrastructure-security-lab/main/7_Projects/01_elastic-squid-web-security/images/02-squid-configuration.png)

- Configure the listening port and Access Control Lists (ACL).
- Add the following lines into the configuration squid file
```bash
acl blocked_domains dstdomain "/etc/squid/blocked_domains.txt"
http_access deny blocked_domains
```
![Squid ACL Configuration](https://raw.githubusercontent.com/cyberxxyyxx/infrastructure-security-lab/main/7_Projects/01_elastic-squid-web-security/images/03-acl_config.png)


### Step 2 – Domain Blocklist

- Create a restricted domains list.
- Configure Squid to read the blocklist.
```bash
sudo nano /etc/squid/blocked_domains.txt
```
![Domain Blocklist](https://raw.githubusercontent.com/cyberxxyyxx/infrastructure-security-lab/main/7_Projects/01_elastic-squid-web-security/images/04-domain-blocklist.png)

- Apply domain filtering rules.
```bash
sudo systemctl reload squid
```
![Network Architecture](7_Projects/01_elastic-squid-web-security/images/05-apply-ruless.png)

## 3. Testing & Validation

- Before Applying ACL Rules - Test access to allowed websites. Access allowed websites through the proxy.
  
![Network Architecture](7_Projects/01_elastic-squid-web-security/images/06-before-applying-ACL-rules.png)
  
- After Applying ACL Rules - Attempt to access restricted domains. Access allowed websites through the proxy.

![Network Architecture](7_Projects/01_elastic-squid-web-security/images/07-after-applying-ACL-rules.png)

![Network Architecture](7_Projects/01_elastic-squid-web-security/images/08-after-applying-ACL-rules-2.png)


### Step 4 – Elastic Security Monitoring

- Verify incoming Squid events.
- 
  Filter by:
```bash
  event.dataset : "squid.log" and squid.status_code : 403
```
![Network Architecture](7_Projects/01_elastic-squid-web-security/images/09-elastic-security-events.png)

- Analyze blocked and allowed requests.

![Network Architecture](7_Projects/01_elastic-squid-web-security/images/10-Elastic-security-events.png)


*This documentation describes a practical cybersecurity lab implemented in a controlled homelab environment.*

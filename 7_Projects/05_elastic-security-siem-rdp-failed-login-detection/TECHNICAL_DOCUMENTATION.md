# Technical Documentation

## Elastic Security SIEM – Security Event Monitoring & RDP Failed Login Detection

### Project Video

[Watch the project demonstration on YouTube](https://www.youtube.com/watch?v=cfCilGGANMQ&t=188s).

---

## 1. Lab Environment

The lab consists of three main systems operating in a segmented network environment.

| Hostname / Component | IP Address | Role | VLAN |
|---|---|---|---|
| KALI-01 | 10.10.30.100 | Security Testing / RDP Authentication Attempts | VLAN 30 |
| WINDOWS-CLIENT | WINDOWS_ENDPOINT_IP | Windows Endpoint / RDP Target | To be confirmed |
| SEC-01 | 10.10.50.10 | Elastic Security SIEM | VLAN 50 |

The environment is hosted on Proxmox VE and uses OPNsense for network segmentation and traffic management.

## 2. Architecture

The Windows endpoint acts as the target system and generates Windows Security Events during authentication attempts.

Kali Linux is used to perform controlled RDP authentication tests against the Windows endpoint.

Failed authentication attempts are recorded in the Windows Security Event Log, including Event ID `4625`.

Elastic Agent collects the relevant Windows Security Events and forwards them to the Elastic Stack infrastructure for centralized monitoring and investigation.

Elastic Security is used to analyze authentication activity, configure detection rules, and generate SIEM alerts.

![Siem RPD](https://raw.githubusercontent.com/cyberxxyyxx/infrastructure-security-lab/main/7_Projects/05_elastic-security-siem-rdp-failed-login-detection/images/00-diagram.png)


### Traffic Flow

1. Kali Linux initiates RDP authentication attempts against the Windows endpoint.
2. The Windows endpoint processes the authentication requests.
3. Failed authentication attempts are recorded in the Windows Security Event Log.
4. Windows generates Event ID `4625` for failed logon attempts.
5. Elastic Agent collects the relevant security events.
6. Collected events are forwarded to the Elastic Stack.
7. Elasticsearch stores and indexes incoming security events.
8. Kibana Discover is used to search and investigate authentication events.
9. Elastic Security evaluates the configured detection rule and generates alerts when its conditions are met.

---

## 3. Implementation Steps

### Step 1 – Lab Environment Preparation

The demonstration was performed from the management laptop.

Access Kali Linux through the management environment.

Verify network connectivity between Kali Linux, the Windows endpoint, and the Elastic Security server.

Access Kali Linux:

```bash
ssh admin@10.10.30.100
```

Verify that the Windows endpoint is reachable and that Remote Desktop is enabled.

### Step 2 – Windows Remote Desktop & Security Event Configuration

Prepare the Windows endpoint to accept RDP connections.

Verify the following configurations:

- Remote Desktop is enabled.
- The Windows Firewall allows the required RDP connections.
- The Windows endpoint is connected to the lab network.
- Windows Security auditing records failed logon events.

Windows Security Event ID `4625` represents a failed logon attempt.

These events provide information about unsuccessful authentication attempts, including the account involved and available source network information.

### Step 3 – RDP Authentication Testing

From KALI-01, initiate controlled RDP authentication attempts against the Windows endpoint.

Use the Windows Remote Desktop client or another suitable RDP client.

Perform multiple failed login attempts using the username `admin` and different passwords.

The objective is to generate Windows authentication failure events for subsequent SIEM analysis.

### Step 4 – Windows Security Event Monitoring

On the Windows endpoint, open Event Viewer.

Navigate to:

```text
Windows Logs → Security
```

Filter or search for Event ID:

```text
4625
```

Review the generated failed logon events.

Pay attention to:

- Account Name
- Source Network Address
- Logon Type
- Failure Information
- Event Timestamp

Verify that the events correspond to the authentication attempts performed from Kali Linux.

### Step 5 – Elastic Security Event Collection

Access Kibana and navigate to Discover.

Verify that Windows Security Events are being received from the monitored endpoint.

Review the incoming authentication events and identify Event ID `4625`.

The following KQL query can be used to filter failed Windows logon events:

```kql
host.name : "WINDOWS-CLIENT" and event.code : "4625"
```

Replace the hostname with the actual hostname configured in the lab.

Investigate relevant fields, including:

- `host.name`
- `source.ip`
- `user.name`
- `event.code`
- `event.outcome`
- `winlog.event_data.LogonType`
- `@timestamp`

### Step 6 – Elastic Security Detection Rule

Configure a custom detection rule in Elastic Security to monitor failed Windows authentication events.

Navigate to:

```text
Security → Rules → Detection Rules
```

Select:

```text
Create a rule → Custom Query
```

Configure the KQL query:

```kql
host.name : "WINDOWS-CLIENT" and event.code : "4625"
```

Replace the hostname with the actual monitored Windows endpoint.

The rule monitors failed logon events generated by the selected Windows endpoint.

Review the rule configuration, execution interval, and alert settings.

After saving the rule, perform additional controlled failed authentication attempts and verify whether Elastic Security generates the expected alerts.

---

## 4. Security Monitoring & Investigation

The investigation focuses on identifying and analyzing failed authentication activity recorded by the Windows endpoint.

The monitoring process includes:

- Identifying failed Windows logon events.
- Investigating Event ID `4625`.
- Identifying the source IP address.
- Reviewing targeted usernames.
- Analyzing authentication timestamps.
- Examining Windows logon types and failure information.
- Monitoring repeated authentication failures.
- Reviewing Elastic Security detection alerts.

The Elastic Security interface provides centralized visibility into the collected authentication events and supports investigation through event details and alert information.

The detection rule provides a practical example of how Windows Security Events can be used to identify and monitor failed authentication activity.

---

## 5. Conclusion

This project demonstrates how Elastic Security SIEM can be used to collect, monitor, and investigate Windows authentication events in a controlled cybersecurity lab environment.

Controlled RDP authentication attempts were used to generate failed logon events on the Windows endpoint.

Windows Security Event ID `4625` provided the relevant authentication failure information, while Elastic Agent collected and forwarded the events to the Elastic Stack.

Kibana Discover enabled centralized event analysis, and a custom Elastic Security detection rule was configured to monitor failed authentication activity and generate SIEM alerts.

The project demonstrates a practical security monitoring workflow, from generating authentication events to collecting telemetry, configuring detection rules, and investigating security alerts.

This documentation describes a practical SIEM monitoring and authentication detection lab implemented in a controlled homelab environment for educational and cybersecurity portfolio purposes.

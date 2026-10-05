# SOC & SIEM Monitoring Lab

## Overview

This project builds a hands on Security Operations Center (SOC) and Security Information and Event Management (SIEM) lab using Wazuh, Sysmon, Windows Security logs, and MITRE ATT&CK.

The lab builds on an Active Directory environment and demonstrates how endpoint telemetry is collected, analyzed, detected, and investigated from a centralized security monitoring platform.

The goal was to gain practical experience with endpoint monitoring, security event analysis, threat detection, and incident investigation.

## Objectives

- Deploy and configure Wazuh as a centralized SIEM platform
- Connect a Windows 11 endpoint to Wazuh
- Collect Windows Security and Sysmon telemetry
- Monitor authentication and account activity
- Detect suspicious PowerShell behavior
- Investigate security alerts and endpoint events
- Map detections to MITRE ATT&CK techniques
- Practice a basic SOC investigation workflow

## Lab Environment

| Component | Configuration |
|---|---|
| SIEM | Wazuh 4.14.8 |
| SIEM Server | Ubuntu Server 24.04 LTS |
| Endpoint | Windows 11 Pro |
| Endpoint Name | CLIENT01 |
| Domain | corp.lab |
| Domain Controller | AD-DC01 |
| Network | VirtualBox NAT + Host-Only |
| Monitoring Agent | Wazuh Agent |
| Endpoint Telemetry | Sysmon + Windows Security Logs |

## Architecture

```text
                 ┌──────────────────────────┐
                 │      Windows 11 Host     │
                 │        VirtualBox        │
                 └────────────┬─────────────┘
                              │
                 ┌────────────┴─────────────┐
                 │                          │
        ┌────────▼────────┐       ┌────────▼────────┐
        │    CLIENT01     │       │   WAZUH-SIEM    │
        │   Windows 11    │       │ Ubuntu Server   │
        │                 │       │                 │
        │ Windows Logs    │       │ Wazuh Manager   │
        │ Sysmon          │──────▶│ Wazuh Indexer   │
        │ Wazuh Agent     │       │ Wazuh Dashboard │
        └─────────────────┘       └─────────────────┘
                 │
                 │
        ┌────────▼────────┐
        │    AD-DC01      │
        │ Windows Server   │
        │ Active Directory │
        │ DNS              │
        └──────────────────┘

```

## Screenshots

### Wazuh Dashboard
![Wazuh Dashboard](screenshots/02-wazuh-dashboard.png)

### Wazuh Agent Connected
![Wazuh Agent Active](screenshots/03-wazuh-agent-active.png)

### Sysmon Endpoint Telemetry
![Sysmon Events](screenshots/04-sysmon-events.png)

### Failed Logon Detection
![Failed Logon Alert](screenshots/07-wazuh-failed-logon-alert.png)

### Failed Login Investigation
![Failed Login Investigation](screenshots/09-failed-login-investigation.png)

### PowerShell Detection
![PowerShell Detection](screenshots/15-wazuh-powershell-detection.png)

### Encoded PowerShell Detection
![Encoded PowerShell Alert](screenshots/12-powershell-encoded-command-alert.png)

### Administrator Account Change
![Administrator Account Enabled](screenshots/16-wazuh-administrator-account-enabled.png)

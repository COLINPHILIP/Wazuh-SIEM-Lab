# Wazuh SIEM Security Monitoring Lab

## Overview

This project demonstrates the deployment and use of Wazuh for security monitoring and threat detection in an isolated virtualized cybersecurity lab.

The lab uses Kali Linux as an attacker, Ubuntu Linux as the monitored endpoint, and Wazuh components for centralized security monitoring, log analysis and alert detection.

## Architecture

Kali Linux
    |
    | SSH authentication attempts
    v
Ubuntu Linux
    |
    | Wazuh Agent
    v
Wazuh Manager
    |
    v
Wazuh Indexer
    |
    v
Wazuh Dashboard

## Lab Environment

| Component | Role |
|---|---|
| Kali Linux | Attack simulation |
| Ubuntu Linux | Monitored endpoint |
| Wazuh Agent | Endpoint telemetry collection |
| Wazuh Manager | Security event analysis |
| Wazuh Indexer | Event storage and indexing |
| Wazuh Dashboard | Security monitoring and investigation |

## Network

| System | IP Address |
|---|---|
| Kali Linux | 192.168.64.6 |
| Ubuntu Victim | 192.168.64.8 |
| Wazuh Manager | 192.168.64.3 |

## Attack Simulation

SSH password-guessing activity was simulated from Kali Linux against the Ubuntu endpoint.

Example:

    Kali Linux
    192.168.64.6
          |
          | SSH authentication attempts
          v
    Ubuntu Linux
    192.168.64.8

The objective was to generate authentication telemetry and validate Wazuh detection.

## Detection Process

The detection pipeline was:

Attack
→ Ubuntu authentication logs
→ Wazuh Agent
→ Wazuh Manager
→ Detection Rules
→ Security Alerts
→ Wazuh Indexer
→ Wazuh Dashboard

## Evidence

The Ubuntu authentication logs recorded multiple failed SSH authentication attempts originating from 192.168.64.6.

Wazuh rules observed during testing included:

- Rule 5557 - password check failure
- Rule 5760 - SSH authentication failure
- Rule 2502 - brute-force detection

## MITRE ATT&CK

The observed activity was associated with:

- T1110.001 - Password Guessing
- T1021.004 - SSH

## Investigation

The source IP, target endpoint, authentication protocol and failed authentication events were investigated using Linux authentication logs and Wazuh security events.

## Skills Demonstrated

- SIEM deployment
- Linux administration
- Security monitoring
- Log analysis
- SSH security
- Brute-force detection
- Endpoint monitoring
- MITRE ATT&CK
- Alert investigation
- Virtualized cybersecurity labs

## Limitations

This project was conducted in an isolated virtualized lab environment and does not represent a production SOC environment.

## Future Improvements

- Windows endpoint monitoring
- Custom Wazuh detection rules
- Active Response
- Suricata integration
- Additional endpoints
- Threat intelligence integration
- Automated incident response

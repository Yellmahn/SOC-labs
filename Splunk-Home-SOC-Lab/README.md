# Enterprise Splunk Monitoring Lab

## Overview

This project is a home SOC (Security Operations Center) lab designed to gain hands-on experience with centralized log management, endpoint monitoring, and security event investigation using Splunk Enterprise.

The lab simulates a small enterprise environment where logs from both Linux and Windows systems are collected, forwarded, indexed, and analyzed through a centralized SIEM platform. The primary objective is to develop practical skills in log collection, endpoint visibility, security monitoring, and Splunk Search Processing Language (SPL), while building a portfolio project that demonstrates real-world security operations concepts.

The environment consists of a Debian Linux virtual machine running Splunk Enterprise and a Windows host machine acting as a monitored endpoint. Splunk Universal Forwarder is deployed on both systems to collect and forward logs to the Splunk server.

### Linux Data Sources

- `/var/log/syslog`
- `/var/log/auth.log`
- `/var/log/dpkg.log`
- `auditd` logs

### Windows Data Sources

- Security Event Log
- System Event Log
- Application Event Log
- Microsoft Sysmon Operational Log

To improve endpoint visibility, Microsoft Sysmon is installed on the Windows endpoint using the SwiftOnSecurity Sysmon configuration. This provides detailed telemetry such as process creation, network connections, registry modifications, DNS queries, and file activity beyond the default Windows Event Logs.

The lab also includes validation exercises where security-relevant activities—such as user account creation, account deletion, authentication events, process execution, and other administrative actions—are intentionally generated and investigated through Splunk searches to verify that logging and monitoring are functioning as expected.

---

## Objectives

- Build a centralized log collection environment using Splunk Enterprise.
- Collect and normalize logs from both Linux and Windows systems.
- Deploy Splunk Universal Forwarder on multiple endpoints.
- Improve Windows endpoint visibility using Microsoft Sysmon.
- Practice writing SPL queries to investigate security events.
- Simulate administrative and security-related activities to validate log collection.
- Develop practical SIEM and SOC analyst skills through hands-on experience.

---

## Technologies Used

- Splunk Enterprise
- Splunk Universal Forwarder
- Debian Linux
- Windows 11
- VMware Workstation
- Microsoft Sysmon
- SwiftOnSecurity Sysmon Configuration
- Linux Audit Framework (auditd)
- SPL (Search Processing Language)

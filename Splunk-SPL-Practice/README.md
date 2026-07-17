# My Splunk Learning Journey

## Introduction

This document summarizes my hands-on journey of learning Splunk Search Processing Language (SPL) and applying it to practical security monitoring and detection engineering. The objective of this project was not only to understand SPL syntax but also to develop the ability to analyze security logs, identify malicious activities, and create effective detection rules for a Security Operations Center (SOC).

Throughout this learning journey, I progressed from understanding basic SPL commands to developing complete detection use cases based on simulated cyber attack scenarios. Each lab includes realistic log data, an SPL detection query, alert configuration, and supporting documentation to demonstrate how common attack techniques can be detected in Splunk.

---

# Learning Journey

## Phase 1 – Learning SPL Fundamentals

The first stage focused on understanding the fundamentals of Splunk Search Processing Language (SPL). I learned how to search indexed data, filter events, extract fields, perform statistical analysis, and manipulate search results using commands such as `search`, `table`, `stats`, `eval`, `where`, `rex`, `lookup`, `eventstats`, and `streamstats`. These commands became the foundation for building more advanced security detections.

---

## Phase 2 – Building Detection Queries

After becoming familiar with SPL, I began developing detection queries for common attack techniques. Each scenario required analyzing the attack behavior, identifying useful log fields, and designing a query capable of detecting suspicious activity while minimizing false positives.

The detection scenarios covered in this project include:

- Password Spraying
- Brute Force Attack
- Impossible Travel
- DNS Tunneling
- Ransomware Activity

Each scenario includes:
- A simulated log dataset
- SPL detection query
- Detection logic
- Splunk alert configuration
- Detection screenshots

---

# Detection Scenarios

## Password Spraying

Detects a single source IP attempting to authenticate against multiple user accounts using the same password. The detection identifies a high number of failed authentication attempts across many unique users within a short period of time.

➡️ See: `./Practice-Scenarios/password-spraying-detection.md`

---

## Brute Force Attack

Detects repeated failed authentication attempts against one or more user accounts from the same source IP. The detection focuses on identifying excessive authentication failures that may indicate password guessing activity.

➡️ See: `labs/02_brute_force.md`

---

## Impossible Travel

Detects successful logins from different countries within an unrealistic time frame. This scenario demonstrates how geographic information and login timestamps can be correlated to identify potential account compromise.

➡️ See: `labs/03_impossible_travel.md`

---

## DNS Tunneling

Detects unusually long DNS queries that may indicate data exfiltration or command-and-control communication over the DNS protocol.

➡️ See: `labs/04_dns_tunneling.md`

---

## Ransomware Activity

Detects abnormal file encryption behavior by identifying hosts generating a high volume of file rename events within a short period of time.

➡️ See: `labs/05_ransomware.md`

---

# Skills Developed

Through this project, I gained practical experience in:

- Writing SPL queries
- Log analysis
- Field extraction
- Statistical analysis using SPL
- Detection engineering
- Splunk alert creation
- Security event investigation
- Documentation of detection logic
- Understanding common cyber attack techniques

---

# Conclusion

This repository represents my practical journey in learning Splunk and detection engineering. Rather than focusing solely on SPL syntax, I emphasized understanding attacker behavior and translating that knowledge into effective detection logic. As I continue learning, additional attack scenarios, detection techniques, and advanced SPL use cases will be added to further expand this project.

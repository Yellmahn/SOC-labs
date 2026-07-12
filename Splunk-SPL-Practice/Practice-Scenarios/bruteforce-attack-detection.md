# Brute Force Attack Detection

## Overview

This lab simulates a **Brute Force** attack against an SSH service. An attacker repeatedly attempts to authenticate to a system by trying multiple passwords against one or more user accounts from the same source IP address. Unlike a password spraying attack, which targets many accounts with a single password, a brute force attack focuses on making numerous authentication attempts until valid credentials are found. The objective of this detection is to identify source IP addresses generating an excessive number of failed authentication attempts within a short period of time. This detection aligns with **MITRE ATT&CK T1110.001 – Password Guessing**.

---

## Log File

`logs/auth_bruteforce.log`

---

## Detection Query

```spl
index="lab-sample" sourcetype="bruteforcelog" "Failed password"
| rex "Failed password for (?<username>\S+) from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| bucket _time span=5m
| stats count dc(username) as unique_users values(username) as usernames by _time src_ip
| where count>=10 OR unique_users>=3
| sort -count
```

---

## Query Explanation

This search monitors failed SSH authentication attempts and groups them into five-minute intervals. It counts the number of failed login attempts and the unique user accounts targeted by each source IP. Source IPs exceeding the configured thresholds are flagged as potential brute force attacks for further investigation.

---

## Detection Result

![Brute Force Detection](../screenshots/bruteforce_detection.png)

# DNS Tunneling Detection

## Overview

This lab simulates a **DNS Tunneling** attack where an attacker uses DNS queries to transfer data between a compromised host and an external server. DNS tunneling often generates unusually long or encoded query names that differ from normal DNS traffic. The objective of this detection is to identify DNS requests with abnormal query lengths, providing an early indicator of potential data exfiltration or command-and-control activity. This detection aligns with **MITRE ATT&CK T1071.004 – DNS**.

---

## Log File

`logs/dns_tunneling.log`

---

## Detection Query

```spl
index="lab-sample" sourcetype="dns-logs"
| eval query_length=len(query)
| where query_length > 50
| table _time src_ip query query_length
```

---

## Query Explanation

This search monitors DNS queries and calculates the length of each requested domain name. It filters queries that exceed the configured length threshold and displays the source IP, queried domain, and query length. Unusually long DNS queries may indicate encoded data being transmitted through DNS and should be investigated for potential DNS tunneling activity.

---

## Detection Result

![DNS Tunneling Detection](../screenshots/dns_tunneling_detection.png)

# Impossible Travel Detection

## Overview

This lab simulates an **Impossible Travel** scenario where a user successfully authenticates from two different countries within an unrealistically short period of time. Such activity may indicate compromised credentials, VPN abuse, or unauthorized account access. The objective of this detection is to identify successful logins from different geographic locations that occur within one hour of each other. This detection aligns with **MITRE ATT&CK T1078 – Valid Accounts**.

---

## Log File

`logs/impossible_travel.log`

---

## Detection Query

```spl
index="lab-sample" sourcetype=imptravel *LOGIN_SUCCESS*
| rex "user=(?<user>\S+)"
| rex "country=(?<country>.+?) city="
| sort 0 user _time
| streamstats current=f last(country) as previous_country last(_time) as previous_time by user
| eval minutes=round((_time-previous_time)/60,2)
| where previous_country!=country AND minutes<=60
| table _time user previous_country country minutes
```

---

## Query Explanation

This search monitors successful login events and extracts the user and country information from each log entry. The events are sorted chronologically for each user, allowing the query to compare the current login with the previous one. It then calculates the time difference between consecutive logins and identifies users who successfully authenticate from different countries within one hour, indicating potential impossible travel activity.

---

## Detection Result

![Impossible Travel Alert](../screenshots/impossible_travel_alert.png)

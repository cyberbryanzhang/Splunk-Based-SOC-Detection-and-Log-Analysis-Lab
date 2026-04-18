# Splunk-Based SOC Detection and Log Analysis Lab

A hands-on SOC-style lab built using Splunk to simulate log ingestion, detection, and basic threat investigation workflows.

---

## 🧭 Project Overview

This project simulates a basic Security Operations Center (SOC) workflow using Splunk.

I worked with authentication and system log data to identify suspicious patterns such as repeated failed logins and abnormal access behavior. The focus was on building detection logic using SPL and understanding how log data can be used to investigate potential security incidents.

This project reflects how a junior SOC analyst would approach log analysis, detection, and investigation.

---

## 🎯 Objectives

- Understand how log data is structured and analyzed in Splunk  
- Develop detection logic for common security scenarios  
- Practice identifying abnormal patterns and suspicious behavior  
- Build a basic investigation workflow using real queries  

---

## ⚙️ Environment Setup

- Splunk Enterprise (local instance)  
- Sample authentication and system logs  
- Local machine (Windows/Linux) used as log source  

---

## 📥 Data Ingestion

Log data was ingested into Splunk using:

- Local file upload  
- Basic sourcetype configuration  
- Indexing for search optimization  

Example log types used:
- Authentication logs  
- System event logs  
- Basic network-related logs  

---

## 🔍 Detection Scenarios

### 🚫 Failed Login Detection
Identified repeated failed login attempts from the same source IP or targeting the same user account.  
High counts within a short time window were treated as potential brute-force indicators.

### 🌙 Suspicious Login Timing
Analyzed login activity outside expected time ranges (e.g., late night or unusual hours) to identify abnormal behavior.

### 🌐 Abnormal IP Activity
Tracked repeated access attempts from specific IP addresses and compared distribution patterns across users.

### 📈 Event Spikes
Monitored sudden increases in authentication events, which may indicate automated or scripted activity.
---

## 🧪 SPL Queries

### Failed Login Detection

```spl
index=* "failed password"
| stats count by src_ip, user
| sort - count
---


🧾 Example Findings

- Observed multiple failed login attempts from a single IP targeting different user accounts  
- Detected spikes in login activity within short time intervals  
- Identified patterns consistent with basic brute-force behavior  

These observations were based on SPL queries and visualized through dashboard panels.


📄 License

This project is licensed under the MIT License. See the LICENSE file for details.

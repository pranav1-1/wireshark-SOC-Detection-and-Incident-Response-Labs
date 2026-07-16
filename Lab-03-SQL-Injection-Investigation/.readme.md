# Lab 03 – SQL Injection Investigation

## Overview

This lab simulates a SQL Injection attack against a vulnerable web application (DVWA) hosted on an Ubuntu server. The objective is to investigate the attack from a Tier-1 SOC Analyst perspective using Wireshark and identify malicious HTTP requests, SQL Injection payloads, and Indicators of Compromise (IOCs).

---

## Incident Scenario

ABC Technologies hosts an internal employee portal on an Ubuntu web server.

The Security Information and Event Management (SIEM) system generated the following alert:

**Alert:** Possible SQL Injection Attempt

A user from an internal workstation attempted to manipulate the web application's database by sending suspicious SQL statements through the login page.

As a Tier-1 SOC Analyst, the objective is to validate the alert, identify the attacker, determine the targeted application, collect evidence, and decide whether escalation is required.

---

## Lab Environment

| Machine | Role | IP Address |
|----------|------|------------|
| Kali Linux | Attacker | 192.168.1.7 |
| Ubuntu + DVWA | Target Web Server | 192.168.1.5 |

---

## Tools Used

- Wireshark
- Firefox
- DVWA (Damn Vulnerable Web Application)
- Apache2
- PHP
- MariaDB
- Kali Linux
- Ubuntu

---

## Skills Practiced

- HTTP Traffic Analysis
- SQL Injection Detection
- Packet Investigation
- HTTP Stream Analysis
- IOC Collection
- Incident Documentation
- Tier-1 SOC Investigation
- MITRE ATT&CK Mapping

---

## Investigation Objectives

- Identify the attacker IP
- Identify the target server
- Find the vulnerable web page
- Analyze the SQL Injection payload
- Inspect HTTP Requests and Responses
- Follow HTTP Stream
- Collect Indicators of Compromise
- Determine incident severity
- Decide whether escalation is required

---

## MITRE ATT&CK

Technique:

**T1190 – Exploit Public-Facing Application**

---

## Indicators of Compromise (IOCs)

- Source IP Address
- Destination IP Address
- HTTP Request URI
- SQL Injection Payload
- HTTP Method
- User-Agent
- Timestamp
- HTTP Response Code

---

## Escalation Decision

Escalate the incident if:

- SQL Injection appears successful.
- Sensitive data is exposed.
- Authentication is bypassed.
- Database errors reveal backend information.
- Multiple SQL Injection attempts are detected.

---

## Learning Outcome

After completing this lab, you will be able to:

- Investigate SQL Injection attacks using Wireshark.
- Analyze malicious HTTP requests.
- Identify SQL Injection payloads.
- Collect Indicators of Compromise (IOCs).
- Perform a Tier-1 SOC investigation.
- Document findings and determine escalation requirements.

---


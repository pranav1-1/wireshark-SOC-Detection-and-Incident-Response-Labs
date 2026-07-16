# Lab 02 – Nmap Reconnaissance Detection

## Overview

This lab demonstrates how a Tier-1 SOC Analyst detects and investigates TCP SYN port scanning performed using Nmap.

---

## Incident Scenario

The SIEM generates an alert indicating possible reconnaissance activity against an internal Ubuntu server.

The objective is to identify scanning behavior, determine targeted services, and document the findings.

---

## Lab Environment

| Machine | Role | IP |
|----------|------|----|
| Kali Linux | Scanner | 192.168.1.7 |
| Ubuntu | Target | 192.168.1.5 |

---

## Tools Used

- Wireshark
- Nmap
- Ubuntu Linux
- Kali Linux

---

## Skills Practiced

- Port Scan Detection
- TCP Flag Analysis
- Reconnaissance Investigation
- IOC Collection
- Incident Documentation
- Tier-1 SOC Investigation

---

## MITRE ATT&CK

Technique:

**T1595 – Active Scanning**

---

## Indicators of Compromise

- Sequential SYN packets
- Multiple destination ports
- High connection rate
- Source IP of scanner
- Target server IP

---

## Escalation Decision

Document reconnaissance activity.

Escalate if scanning is unauthorized or followed by exploitation attempts.

---

## Learning Outcome

Learn how Wireshark and TCP analysis help identify reconnaissance activities commonly observed before cyberattacks.

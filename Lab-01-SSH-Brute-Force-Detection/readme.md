# Lab 01 – SSH Brute Force Detection

## Overview

This lab simulates an SSH brute-force attack against an Ubuntu server using Hydra. The objective is to investigate the attack from a Tier-1 SOC Analyst perspective using Wireshark and Linux authentication logs.

---

## Incident Scenario

A SIEM alert reports multiple failed SSH login attempts against an internal Ubuntu server.

As a Tier-1 SOC Analyst, the goal is to:

- Validate the alert
- Identify the attacker and victim
- Analyze network traffic
- Verify authentication attempts
- Collect Indicators of Compromise (IOCs)
- Assess severity
- Decide whether escalation is required

---

## Lab Environment

| Machine | Role | IP |
|----------|------|----|
| Kali Linux | Attacker | 192.168.1.7 |
| Ubuntu | Target | 192.168.1.5 |

---

## Tools Used

- Wireshark
- Hydra
- OpenSSH Server
- Ubuntu Linux
- Kali Linux

---

## Skills Practiced

- SSH Traffic Analysis
- Brute Force Detection
- TCP Packet Analysis
- IOC Collection
- Authentication Log Analysis
- Incident Documentation
- Tier-1 SOC Investigation

---

## MITRE ATT&CK

Technique:

**T1110 – Brute Force**

---

## Indicators of Compromise

- Multiple SSH connection attempts
- Repeated TCP connections to Port 22
- High authentication failure rate
- Source IP of attacker
- Target Ubuntu server

---

## Escalation Decision

If authentication fails repeatedly, document the activity and recommend escalation according to company policy.

If authentication succeeds, immediately escalate the incident to Tier-2 SOC.

---

## Learning Outcome

Understand how a Tier-1 SOC Analyst investigates SSH brute-force attacks using packet captures and authentication logs.

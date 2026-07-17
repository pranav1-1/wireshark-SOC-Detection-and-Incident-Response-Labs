# SOC Detection and Incident Response

> A hands-on Security Operations Center (SOC) portfolio project focused on detecting, analyzing, and investigating real-world cyber attacks using Wireshark in a controlled home lab environment.

---

## About the Project

**SOC Detection and Incident Response** is a practical cybersecurity project designed to simulate common attack techniques encountered in enterprise environments. The objective is to develop the skills required of a Tier-1 Security Operations Center (SOC) Analyst by performing network traffic analysis, identifying malicious activities, collecting Indicators of Compromise (IOCs), and documenting investigations.

Each lab follows the incident response lifecycle—from attack simulation and packet capture to investigation, evidence collection, and incident reporting.

All activities were performed in an isolated virtual lab using Kali Linux and Ubuntu Server.

---

# Project Objectives

- Perform real-world SOC investigations
- Detect network-based cyber attacks
- Analyze network traffic using Wireshark
- Investigate suspicious protocols and communications
- Identify Indicators of Compromise (IOCs)
- Practice Tier-1 SOC Analyst workflows
- Improve incident response and documentation skills
- Build a professional cybersecurity portfolio

---

# Home Lab Environment

| Component | Details |
|-----------|---------|
| Attacker Machine | Kali Linux |
| Target Machine | Ubuntu Server |
| Network | VirtualBox Internal Network |
| Packet Analyzer | Wireshark |
| Web Server | Apache2 |
| Vulnerable Application | DVWA |
| HTTP Beacon Server | Flask |
| DNS Tunnel Tool | Iodine |
| Reverse Shell Listener | Netcat |

---

# Investigation Workflow

```
Alert Generated
       │
       ▼
Packet Capture
       │
       ▼
Traffic Analysis
       │
       ▼
Protocol Investigation
       │
       ▼
IOC Collection
       │
       ▼
Evidence Documentation
       │
       ▼
Incident Classification
       │
       ▼
Tier-2 Escalation (If Required)
```

---

# Labs Completed

| Lab | Detection Scenario | Protocol |
|------|--------------------|----------|
| Lab 01 | SSH Brute Force Detection | SSH / TCP |
| Lab 02 | Nmap Reconnaissance Detection | TCP |
| Lab 03 | SQL Injection Investigation | HTTP |
| Lab 04 | Web Shell Upload Detection | HTTP |
| Lab 05 | Reverse Shell Detection | TCP |
| Lab 06 | Malware Download Detection | HTTP |
| Lab 07 | DNS Tunneling Detection | DNS |
| Lab 08 | HTTP Beaconing Detection | HTTP |

---

# Skills Developed

- Network Traffic Analysis
- Packet Inspection
- Incident Response
- Threat Hunting
- IOC Collection
- Network Forensics
- Wireshark Analysis
- HTTP Investigation
- DNS Investigation
- TCP Analysis
- Malware Traffic Analysis
- Reverse Shell Detection
- Web Attack Investigation
- SOC Documentation

---

# MITRE ATT&CK Techniques Covered

| Technique | Description | Lab |
|-----------|-------------|-----|
| T1110 | Brute Force | Lab 01 |
| T1595 | Active Scanning | Lab 02 |
| T1190 | Exploit Public-Facing Application | Lab 03 |
| T1505.003 | Web Shell | Lab 04 |
| T1059 | Command and Scripting Interpreter | Lab 05 |
| T1105 | Ingress Tool Transfer | Lab 06 |
| T1071.004 | DNS Protocol | Lab 07 |
| T1071.001 | Web Protocols | Lab 08 |

---

# Tools Used

- Wireshark
- Kali Linux
- Ubuntu Server
- Apache2
- DVWA
- Python
- Flask
- Netcat
- Iodine
- Nmap
- SQLMap
- Bash

---

# Repository Structure

```
SOC-Detection-and-Incident-Response/
│
├── README.md
│
├── Lab-01-SSH-Brute-Force-Detection/
├── Lab-02-Nmap-Reconnaissance-Detection/
├── Lab-03-SQL-Injection-Investigation/
├── Lab-04-Web-Shell-Upload-Detection/
├── Lab-05-Reverse-Shell-Detection/
├── Lab-06-Malware-Download-Detection/
├── Lab-07-DNS-Tunneling-Detection/
└── Lab-08-HTTP-Beaconing-Detection/
```

---

# Learning Outcomes

By completing these labs, I gained practical experience in:

- Detecting common attack techniques using network traffic
- Investigating incidents from a Tier-1 SOC Analyst perspective
- Analyzing HTTP, TCP, SSH, and DNS protocols
- Identifying malicious patterns and Indicators of Compromise (IOCs)
- Following a structured incident response workflow
- Creating professional investigation reports and documentation

---

# Future Labs

The project will continue with additional detection and incident response scenarios, including:

- SMB Lateral Movement Investigation
- Ransomware Activity Detection
- IOC-Based Incident Investigation
- Wazuh Detection & Alert Investigation
- Splunk Detection & Incident Response

---

# Disclaimer

All activities in this repository were performed in a controlled and isolated virtual laboratory for educational and defensive cybersecurity purposes only. No unauthorized systems or production environments were targeted.

---

# Author

**Pranav R Pillai**

**M.Sc. Cyber Forensics & Information Security**

**SOC Analyst | Blue Team | Incident Response**

GitHub: https://github.com/pranav1-1

LinkedIn: *(Add your LinkedIn profile URL)*

---

⭐ **If you found this project useful, consider starring the repository. Feedback and contributions are always welcome.**

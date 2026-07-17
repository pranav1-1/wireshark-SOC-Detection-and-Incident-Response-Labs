# Lab 04 – Web Shell Upload Detection & Investigation

## Overview

This lab demonstrates how a SOC Analyst investigates a suspicious file upload to a web application.

A vulnerable DVWA application was hosted on an Ubuntu server. A file upload was performed from Kali Linux to generate HTTP POST traffic. The network traffic was captured in Wireshark and investigated as if it were a real SOC incident.

---

# Lab Objective

- Understand HTTP POST requests
- Investigate file upload traffic
- Identify uploaded files
- Inspect HTTP headers
- Analyze HTTP responses
- Collect Indicators of Compromise (IOCs)
- Decide whether the incident should be escalated

---

# Lab Environment

| Machine | Role | IP Address |
|----------|------|------------|
| Ubuntu | DVWA Web Server | 192.168.1.5 |
| Kali Linux | Client / Analyst | 192.168.1.7|
| Wireshark | Packet Capture | Kali |

---

# Tools Used

- Kali Linux
- Ubuntu Server
- DVWA
- Apache2
- PHP
- Wireshark
- Firefox

---

# Network Topology

Kali Linux
↓

HTTP POST Request

↓

Ubuntu (DVWA)

↓

HTTP Response

↓

Wireshark Capture

---

# Steps Performed

## Step 1 – Start the Ubuntu Web Server

Verified that Apache and DVWA were running on Ubuntu.

Verified the website by opening:

http://192.168.1.5/dvwa

---

## Step 2 – Start Wireshark

Selected the active network adapter.

Started packet capture before accessing DVWA.

---

## Step 3 – Access DVWA

Opened Firefox on Kali.

Navigated to

http://192.168.1.5/dvwa

Logged into DVWA.

---

## Step 4 – Navigate to File Upload Module

Opened the DVWA File Upload page.

Prepared a sample file for upload.

---

## Step 5 – Upload the Test File

Selected the sample file.

Clicked Upload.

This generated an HTTP POST request.

---

## Step 6 – Stop Packet Capture

Stopped Wireshark after the upload completed.

Saved the capture.

Example:

Lab04_WebShell_Upload.pcapng

---

# Wireshark Investigation

## Display Filters Used

HTTP Traffic

```
http
```

HTTP POST Requests

```
http.request.method == "POST"
```

HTTP Responses

```
http.response
```

Traffic to Ubuntu Server

```
ip.addr == 192.168.1.5
```

TCP Stream

Right Click

Follow

↓

TCP Stream

---

# Packet Analysis

During investigation, inspect the following fields:

- Source IP
- Destination IP
- Source Port
- Destination Port
- HTTP Method
- URI
- Host Header
- Content-Type
- Content-Length
- Server Response
- HTTP Status Code

---



---

# Indicators of Compromise (IOC)

Source IP

Destination IP

HTTP Method

URI

Uploaded File Name

Destination Port

Timestamp

HTTP Status Code

---

# MITRE ATT&CK

T1505.003

Web Shell

---

# SOC Tier-1 Responsibilities

✔ Validate the alert

✔ Analyze HTTP POST traffic

✔ Verify uploaded filename

✔ Collect IOCs

✔ Preserve evidence

✔ Escalate to Tier-2 if malicious upload is confirmed

---

# Skills Learned

- HTTP Protocol Analysis
- HTTP POST Investigation
- File Upload Analysis
- HTTP Header Analysis
- IOC Collection
- Packet Analysis using Wireshark
- SOC Tier-1 Investigation Workflow

---

# Conclusion

The simulated file upload generated HTTP POST traffic that was successfully captured and analyzed using Wireshark. The investigation identified the upload request, server response, source and destination hosts, and other important network artifacts. This lab demonstrates how a Tier-1 SOC Analyst investigates suspicious file upload activity before escalating the incident for deeper forensic analysis.

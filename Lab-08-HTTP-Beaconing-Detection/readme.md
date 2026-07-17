# Lab 08 – HTTP Beaconing Detection & Investigation

## Overview

This lab demonstrates how a Tier-1 SOC Analyst investigates periodic HTTP communication that resembles malware Command-and-Control (C2) beaconing.

A Python client running on Ubuntu periodically sent HTTP GET requests to a Flask web server running on Kali Linux every 10 seconds. Wireshark captured the generated traffic, allowing investigation of repeated HTTP requests, timing patterns, and Indicators of Compromise (IOCs).

The lab simulates the type of network behavior commonly associated with malware beaconing while remaining entirely within an isolated home lab.

---

# Lab Objective

- Understand HTTP Beaconing
- Analyze repeated HTTP GET requests
- Detect periodic communication
- Inspect HTTP headers
- Analyze HTTP responses
- Collect Indicators of Compromise (IOCs)
- Practice Tier-1 SOC investigation workflow

---

# Lab Environment

| Machine | Role | IP Address |
|----------|------|------------|
| Ubuntu | Beacon Client | 192.168.1.5 |
| Kali Linux | Flask HTTP Server | 192.168.1.7 |
| Wireshark | Packet Capture | Kali |

---

# Tools Used

- Kali Linux
- Ubuntu
- Python
- Flask
- Requests Library
- Wireshark

---

# Network Topology

Ubuntu (192.168.1.5)

↓

HTTP GET /check-in

↓

TCP Port 8080

↓

Kali Flask Server (192.168.1.7)

↓

HTTP 200 OK

↓

Wireshark Capture

↓

SOC Investigation

---

# Steps Performed

## Step 1 – Create the Flask Server

Created a Flask application (server.py) on Kali Linux.

The application listened on TCP port 8080 and responded with "OK" whenever a GET request was received on the `/check-in` endpoint.

Verified that the server was running successfully.

---

## Step 2 – Create the Beacon Client

Created a Python script (beacon.py) on Ubuntu.

The client periodically sent HTTP GET requests to:

http://192.168.1.7:8080/check-in

at 10-second intervals.

---

## Step 3 – Start Packet Capture

Started Wireshark on Kali before launching the beacon client.

Captured all HTTP traffic exchanged between Ubuntu and Kali.

---

## Step 4 – Verify Communication

Observed repeated log entries on the Flask server.

Confirmed that each request received an HTTP 200 OK response.

---

## Step 5 – Stop Packet Capture

Stopped Wireshark after several beacon requests.

Saved the capture as:

Lab08_HTTP_Beaconing_Detection.pcapng

---

# Wireshark Investigation

## Display Filters

HTTP

```
http
```

HTTP Requests

```
http.request
```

HTTP Responses

```
http.response
```

GET Requests

```
http.request.method=="GET"
```

Beacon Client

```
ip.src==192.168.1.5
```

Flask Server

```
ip.dst==192.168.1.7
```

TCP Port

```
tcp.port==8080
```

---

# Packet Analysis

Investigated

- Source IP
- Destination IP
- HTTP Method
- Request URI
- Host Header
- User-Agent
- HTTP Response
- Status Code
- Packet Timing
- Request Interval

---


---

# Indicators of Compromise

- Source IP
- Destination IP
- Protocol
- Destination Port
- URI
- User-Agent
- HTTP Status Code
- Timestamp
- Request Interval

---

# MITRE ATT&CK

T1071.001 – Application Layer Protocol: Web Protocols

T1071 – Application Layer Protocol

---

# Tier-1 SOC Responsibilities

✔ Validate SIEM alert

✔ Identify beaconing host

✔ Identify destination server

✔ Verify repeated HTTP GET requests

✔ Measure request interval

✔ Collect Indicators of Compromise

✔ Preserve packet capture

✔ Escalate to Tier-2

---

# Skills Learned

- HTTP Traffic Analysis
- Beacon Detection
- HTTP Header Analysis
- Packet Timing Analysis
- IOC Collection
- Wireshark Investigation
- SOC Tier-1 Workflow

---

# Conclusion

The simulated HTTP beacon generated repeated GET requests from the Ubuntu client to the Kali Flask server every 10 seconds. Wireshark analysis confirmed the periodic communication pattern, HTTP responses, and associated indicators of compromise. This lab demonstrates how a SOC Tier-1 Analyst investigates beaconing behavior commonly associated with Command-and-Control (C2) communications.

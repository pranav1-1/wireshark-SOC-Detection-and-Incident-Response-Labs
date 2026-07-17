# Incident Report

## Incident Name

HTTP Beaconing Detection Investigation

---

## Incident ID

SOC-LAB-08

---

## Severity

High

---

## Analyst

Pranav R Pillai

---

# Executive Summary

A SIEM alert reported repeated HTTP requests originating from an internal Ubuntu workstation.

The investigation focused on determining whether the observed communication represented automated HTTP beaconing. Packet capture analysis confirmed periodic HTTP GET requests from the Ubuntu client to a Flask server hosted on Kali Linux within the isolated lab environment.

---

# Lab Environment

Beacon Client

Ubuntu

IP Address

192.168.1.5

Server

Kali Linux (Flask)

IP Address

192.168.1.7

Protocol

HTTP

Port

8080

---

# Investigation Timeline

1. Started Flask server on Kali.
2. Started beacon client on Ubuntu.
3. Began Wireshark capture.
4. Generated periodic HTTP requests.
5. Captured network traffic.
6. Stopped capture.
7. Investigated HTTP packets.
8. Collected Indicators of Compromise.

---

# Investigation Performed

## HTTP Request Analysis

Applied:

```
http.request
```

Verified:

- Source IP
- Destination IP
- HTTP Method
- Request URI
- Host Header
- User-Agent

---

## HTTP Response Analysis

Observed:

```
HTTP/1.1 200 OK
```

Confirmed that each HTTP GET request received a successful response.

---

## Traffic Pattern Analysis

Measured packet timestamps and identified a consistent 10-second interval between requests, indicating automated communication rather than typical user browsing.

---

## HTTP Stream Analysis

Used **Follow → HTTP Stream** to reconstruct the complete HTTP request and response sequence.

---

# Indicators of Compromise

| IOC | Value |
|------|-------|
| Client IP | 192.168.1.5 |
| Server IP | 192.168.1.7 |
| Protocol | HTTP |
| Destination Port | 8080 |
| Method | GET |
| URI | /check-in |
| Status Code | 200 OK |
| Request Interval | 10 Seconds |

---

# Evidence Collected

- PCAP File
- HTTP GET Requests
- HTTP Responses
- HTTP Stream
- Conversation Statistics
- Endpoint Statistics
- Wireshark Screenshots

---

# SOC Tier-1 Assessment

The investigation confirmed repeated HTTP GET requests from the Ubuntu workstation to the Kali Flask server at fixed 10-second intervals. This communication pattern resembles HTTP beaconing because the requests were automated, repetitive, and consistently targeted the same URI.

The activity was expected in this isolated lab because it was intentionally generated for educational purposes. In a production environment, unexplained beaconing behavior would require escalation for further endpoint analysis and threat hunting.

---

# Recommendations

- Monitor repeated HTTP requests to the same URI.
- Identify hosts generating regular outbound web traffic.
- Correlate network events with endpoint logs.
- Alert on long-running periodic HTTP sessions.
- Investigate unknown or suspicious User-Agent values.

---

# Lessons Learned

- Analyze HTTP GET requests in Wireshark.
- Detect periodic beaconing using packet timestamps.
- Validate HTTP responses.
- Collect and document network-based IOCs.
- Follow the Tier-1 SOC investigation workflow.

---

# Conclusion

This lab successfully demonstrated HTTP beaconing detection using Wireshark. The investigation identified periodic HTTP communication between the Ubuntu client and Kali Flask server, analyzed request timing, documented Indicators of Compromise, and followed the standard Tier-1 SOC investigation process. The exercise provides practical experience in recognizing network behaviors commonly associated with Command-and-Control (C2) communications.

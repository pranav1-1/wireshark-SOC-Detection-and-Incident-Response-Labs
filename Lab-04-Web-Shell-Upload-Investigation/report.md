# Incident Report

## Incident Name

Web Shell Upload Detection Investigation

---

## Incident ID

SOC-LAB-04

---

## Severity

High

---

## Date

(Add Date)

---

## Analyst

Pranav R Pillai

---

# Executive Summary

A SIEM alert reported a possible malicious file upload to an internal web server.

The investigation focused on analyzing HTTP POST traffic between the client and the Ubuntu DVWA server. The objective was to determine whether a file upload occurred and to collect evidence required for incident escalation.

---

# Lab Environment

Client

Kali Linux

Server

Ubuntu Server (DVWA)

Server IP

192.168.1.5

Protocol

HTTP

---

# Investigation Timeline

1. Started Wireshark capture.

2. Accessed DVWA.

3. Opened File Upload page.

4. Uploaded a sample file.

5. Captured HTTP POST traffic.

6. Stopped capture.

7. Investigated packets.

8. Collected Indicators of Compromise.

---

# Investigation Performed

## Packet Inspection

Verified:

- Source IP
- Destination IP
- TCP Session
- HTTP POST Request
- Request URI
- Host Header
- HTTP Headers
- Content Length
- HTTP Status Code

---

## HTTP Request Analysis

Observed an HTTP POST request containing file upload data directed to the Ubuntu DVWA server.

The upload generated normal HTTP communication and was successfully recorded in the packet capture.

---

## HTTP Response Analysis

Server responded with:

HTTP/1.1 200 OK

This confirmed successful processing of the upload request.

---

# Indicators of Compromise

| IOC | Value |
|------|-------|
| Source IP | Kali Linux |
| Destination IP | 192.168.1.5 |
| Protocol | HTTP |
| Method | POST |
| Destination Port | 80 |
| URI | DVWA Upload Page |
| Status Code | 200 OK |

---

# Evidence Collected

✔ PCAP File

✔ HTTP POST Packet

✔ HTTP Response

✔ TCP Stream

✔ Screenshots

---

# SOC Tier-1 Assessment

The upload activity was confirmed through HTTP POST traffic.

All evidence was documented.

No additional malicious behavior was observed during this controlled lab.

The incident was documented and prepared for escalation according to SOC procedures.

---

# Recommendations

- Enable file upload restrictions.

- Validate uploaded file types.

- Deploy Web Application Firewall (WAF).

- Monitor repeated upload attempts.

- Review web server logs for similar activity.

---

# Lessons Learned

- Identify HTTP POST requests quickly.

- Analyze upload-related traffic.

- Verify HTTP responses.

- Collect network-based IOCs.

- Follow the SOC investigation workflow.

---

# Conclusion

The lab successfully simulated a suspicious file upload to a vulnerable web application. Wireshark analysis enabled identification of the HTTP POST request, verification of the server response, and collection of network artifacts required for SOC investigation. The exercise demonstrates the workflow a Tier-1 SOC Analyst follows when investigating potential web shell upload activity.

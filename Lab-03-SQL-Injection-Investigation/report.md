# SQL Injection Investigation Report

## Incident Summary

The Security Information and Event Management (SIEM) system generated an alert indicating possible SQL Injection activity targeting the company's internal web application.

A packet capture (PCAP) was analyzed to determine whether the alert represented malicious activity.

---

# Investigation Details

**Incident Type**

SQL Injection Attempt

**Severity**

High

**Protocol**

HTTP

**Target Application**

DVWA (Damn Vulnerable Web Application)

---

# Lab Environment

| Machine | Role | IP Address |
|----------|------|------------|
| Kali Linux | Attacker | 192.168.1.7 |
| Ubuntu + DVWA | Target | 192.168.1.5 |

---

# Investigation Steps

1. Opened the PCAP file in Wireshark.
2. Applied HTTP display filter.
3. Identified the suspicious HTTP request.
4. Determined the source IP address.
5. Determined the destination IP address.
6. Inspected the HTTP Request URI.
7. Identified the SQL Injection payload.
8. Reviewed the HTTP response.
9. Followed the HTTP Stream.
10. Collected Indicators of Compromise.
11. Assessed incident severity.
12. Documented findings.

---

# Findings

## Attacker IP

192.168.1.7

---

## Target Server

192.168.1.5

---

## Attack Type

SQL Injection

---

## Protocol

HTTP

---

## HTTP Method

GET / POST

---

## Target URI

/DVWA/vulnerabilities/sqli/

---

## SQL Injection Payload

Example:

' OR 1=1 --

or

1' OR '1'='1

---

## HTTP Response

HTTP/1.1 200 OK

(Response may vary depending on the application.)

---

# Indicators of Compromise (IOCs)

- Source IP Address
- Destination IP Address
- Target URI
- SQL Injection Payload
- HTTP Method
- User-Agent
- Timestamp
- HTTP Status Code

---

# MITRE ATT&CK

Technique:

T1190 – Exploit Public-Facing Application

---

# Severity Assessment

**Severity:** High

Reason:

- The attack targets a public-facing web application.
- SQL Injection may expose sensitive database information.
- Successful exploitation can lead to unauthorized access or data theft.

---

# Tier-1 SOC Analyst Actions

- Validated the SIEM alert.
- Confirmed suspicious SQL Injection payload.
- Identified attacker and target.
- Collected network evidence.
- Documented Indicators of Compromise.
- Reviewed HTTP responses.
- Determined incident severity.
- Recommended escalation if exploitation appeared successful.

---

# Escalation Recommendation

Escalate to Tier-2 SOC if:

- Database records are exposed.
- Authentication bypass is observed.
- Multiple SQL Injection attempts are detected.
- Sensitive systems are affected.

---

# Conclusion

The investigation identified HTTP requests containing SQL Injection payloads targeting the DVWA application hosted on the Ubuntu server. Analysis of network traffic confirmed malicious input consistent with SQL Injection techniques. All relevant Indicators of Compromise were documented, and the incident was assessed as High severity pending further application and database log analysis.

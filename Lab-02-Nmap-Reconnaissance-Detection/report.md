# Nmap Reconnaissance Detection Investigation Report

## Incident Summary

The SIEM detected multiple TCP SYN packets targeting different ports on an internal Ubuntu server.

---

## Investigation Steps

1. Verified connectivity.
2. Started packet capture.
3. Executed an Nmap SYN scan.
4. Stopped packet capture.
5. Applied TCP SYN filters.
6. Identified source and destination IP addresses.
7. Examined TCP flags.
8. Identified scanned ports.
9. Collected Indicators of Compromise.
10. Determined incident severity.

---

## Findings

Scanner:
192.168.1.7

Target:
192.168.1.5

Attack Technique:
TCP SYN Port Scan

Protocol:
TCP

---

## Indicators of Compromise

- Multiple SYN packets
- Sequential destination ports
- Reconnaissance pattern
- Source IP
- Destination IP

---

## Severity

Medium

---

## Tier-1 Analyst Decision

The observed traffic is consistent with reconnaissance activity. No exploitation was detected during this investigation.

The incident should be documented and escalated if organizational policy requires further validation or if additional malicious activity follows.

---

## MITRE ATT&CK

T1595 – Active Scanning

---

## Conclusion

Analysis of the packet capture confirmed that the source host performed a TCP SYN scan against multiple ports on the Ubuntu server. The activity is indicative of network reconnaissance commonly performed before exploitation attempts.

# Incident Report

## Incident Name

DNS Tunneling Detection Investigation

---

## Incident ID

SOC-LAB-07

---

## Severity

Critical

---

## Analyst

Pranav R Pillai

---

# Executive Summary

A SIEM alert reported excessive DNS traffic originating from an internal Ubuntu workstation.

The investigation focused on determining whether the observed DNS communication represented DNS tunneling. Packet capture analysis confirmed repeated DNS queries between the Ubuntu client and Kali DNS server in a controlled laboratory environment.

---

# Lab Environment

Client

Ubuntu

IP Address

192.168.1.7

DNS Server

Kali Linux

IP Address

192.168.1.4

Protocol

DNS

Port

UDP 53

---

# Investigation Timeline

1. Started Iodine DNS server.
2. Connected Iodine client.
3. Verified tunnel connectivity.
4. Started Wireshark capture.
5. Captured DNS traffic.
6. Stopped packet capture.
7. Investigated DNS packets.
8. Collected Indicators of Compromise.

---

# Investigation Performed

## DNS Query Analysis

Applied:

```
dns
```

Verified:

- Source IP
- Destination IP
- Query Name
- Query Type
- Transaction ID

---

## Traffic Pattern Analysis

Observed a high volume of DNS queries exchanged between the client and server.

Reviewed packet timing and query frequency to identify repetitive communication patterns.

---

## DNS Response Analysis

Verified successful responses corresponding to the generated DNS queries.

---

# Indicators of Compromise

| IOC | Value |
|------|-------|
| Client IP | 192.168.1.7 |
| DNS Server | 192.168.1.4 |
| Protocol | DNS |
| Destination Port | UDP 53 |
| Tunnel Domain | Configured Iodine Domain |
| Evidence | DNS Queries and Responses |

---

# Evidence Collected

- PCAP File
- DNS Query Packets
- DNS Response Packets
- UDP Conversations
- Endpoint Statistics
- Wireshark Screenshots

---

# SOC Tier-1 Assessment

The investigation confirmed continuous DNS communication between the Ubuntu client and the Kali DNS server. Packet analysis identified repetitive DNS queries consistent with the configured DNS tunnel used in this isolated lab.

The activity was expected because the tunnel was intentionally created for educational purposes. In a production environment, similar unexplained behavior would require escalation for further investigation.

---

# Recommendations

- Monitor abnormal DNS query volumes.
- Investigate long or random DNS query names.
- Restrict unauthorized external DNS servers.
- Correlate DNS activity with endpoint telemetry.
- Deploy IDS/IPS signatures for DNS tunneling detection.

---

# Lessons Learned

- Analyze DNS queries using Wireshark.
- Recognize repetitive DNS communication.
- Identify indicators associated with DNS tunneling.
- Document network-based IOCs.
- Follow the Tier-1 SOC investigation workflow.

---

# Conclusion

This lab successfully demonstrated DNS tunneling detection using Wireshark. The investigation validated DNS tunnel traffic, identified the communicating hosts, analyzed DNS packets, and documented indicators of compromise. The exercise provided practical experience in investigating one of the most common covert communication techniques encountered by SOC analysts.

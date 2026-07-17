# Lab 07 – DNS Tunneling Detection & Investigation

## Overview

This lab demonstrates how a Tier-1 SOC Analyst investigates DNS tunneling activity using Wireshark.

A DNS tunnel was established between an Ubuntu client and a Kali Linux server using Iodine in an isolated lab environment. The generated DNS traffic was captured and analyzed to identify characteristics commonly associated with DNS tunneling.

The investigation focused on analyzing DNS queries, identifying abnormal query names, collecting Indicators of Compromise (IOCs), and determining whether the activity should be escalated.

---

# Lab Objective

- Understand DNS tunneling
- Capture DNS tunnel traffic
- Analyze DNS packets
- Inspect DNS query names
- Identify abnormal DNS behavior
- Collect Indicators of Compromise (IOCs)
- Practice Tier-1 SOC investigation

---

# Lab Environment

| Machine | Role | IP Address |
|----------|------|------------|
| Ubuntu | DNS Tunnel Client | 192.168.1.5|
| Kali Linux | DNS Tunnel Server | 192.168.1.7 |
| Wireshark | Packet Capture | Kali |

---

# Tools Used

- Kali Linux
- Ubuntu
- Iodine
- Wireshark

---

# Network Topology

Ubuntu (192.168.1.7)

↓

DNS Tunnel

↓

UDP Port 53

↓

Kali Linux (192.168.1.4)

↓

Wireshark Capture

↓

SOC Investigation

---

# Steps Performed

## Step 1 – Start the DNS Tunnel Server

Started the Iodine DNS server on Kali Linux.

Verified that the server was listening for DNS tunnel connections.

---

## Step 2 – Connect the DNS Tunnel Client

Started the Iodine client on Ubuntu.

Verified that the tunnel was successfully established.

---

## Step 3 – Verify Connectivity

Tested communication through the tunnel by sending ICMP packets to the tunnel interface.

Confirmed successful communication between the client and server.

---

## Step 4 – Capture Network Traffic

Started Wireshark before establishing the tunnel.

Captured all DNS traffic generated during the session.

---

## Step 5 – Stop Packet Capture

Stopped Wireshark after completing the investigation.

Saved the capture as:

Lab07_DNS_Tunneling_Detection.pcapng

---

# Wireshark Investigation

## Display Filters

DNS Traffic

```
dns
```

DNS Queries

```
dns.flags.response == 0
```

DNS Responses

```
dns.flags.response == 1
```

UDP Port 53

```
udp.port == 53
```

Source Host

```
ip.src == 192.168.1.7
```

Destination Host

```
ip.dst == 192.168.1.4
```

---

# Packet Analysis

Investigated

- Source IP
- Destination IP
- DNS Query Name
- DNS Query Type
- Transaction ID
- UDP Port
- DNS Responses
- Packet Timing
- Query Frequency

---



---

# Indicators of Compromise

- Source IP
- Destination IP
- Domain Name
- DNS Query Type
- Protocol
- Destination Port
- Timestamp
- Query Frequency

---

# MITRE ATT&CK

T1071.004 – Application Layer Protocol: DNS

T1048 – Exfiltration Over Alternative Protocol

T1001 – Data Obfuscation

---

# Tier-1 SOC Responsibilities

✔ Validate SIEM alert

✔ Identify DNS client

✔ Identify DNS server

✔ Analyze DNS query names

✔ Verify abnormal query frequency

✔ Collect IOCs

✔ Preserve evidence

✔ Escalate to Tier-2

---

# Skills Learned

- DNS Packet Analysis
- DNS Tunneling Detection
- Wireshark Investigation
- IOC Collection
- DNS Traffic Analysis
- SOC Tier-1 Investigation Workflow

---

# Conclusion

The DNS tunnel generated continuous DNS queries between the Ubuntu client and Kali server. Wireshark analysis identified the communicating hosts, DNS query patterns, and packet frequency. The investigation demonstrated how a Tier-1 SOC Analyst validates suspicious DNS activity, collects evidence, and prepares the incident for escalation.

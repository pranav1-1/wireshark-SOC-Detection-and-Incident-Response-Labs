# Incident Report

## Incident Name

Reverse Shell Detection Investigation

---

## Incident ID

SOC-LAB-05

---

## Severity

Critical

---

## Analyst

Pranav R Pillai

---

# Executive Summary

A SIEM alert reported a suspicious outbound TCP connection from an internal Ubuntu workstation.

The investigation focused on determining whether the connection represented a reverse shell. Packet capture analysis confirmed an interactive TCP session established between the Ubuntu workstation and a Kali Linux system.

---

# Lab Environment

Victim

Ubuntu

IP Address

192.168.1.5

Attacker

Kali Linux

IP Address

192.168.1.7

Protocol

TCP

Port

4444

---

# Investigation Timeline

1. Started Wireshark capture.

2. Started Netcat listener on Kali.

3. Executed Bash reverse shell from Ubuntu.

4. Verified successful shell connection.

5. Captured all TCP traffic.

6. Analyzed packets.

7. Collected Indicators of Compromise.

---

# Investigation Performed

## TCP Handshake Analysis

Verified the complete three-way handshake.

- SYN
- SYN/ACK
- ACK

The handshake confirmed successful establishment of the TCP session.

---

## Session Analysis

Applied filter

```
tcp.port == 4444
```

Observed continuous PSH/ACK packets carrying interactive shell traffic.

The packet timing and payload confirmed an active remote command session.

---

## TCP Stream Analysis

Used Follow TCP Stream to reconstruct the communication.

Verified execution of Linux shell commands transmitted between the victim and attacker.

---

# Indicators of Compromise

| IOC | Value |
|------|-------|
| Victim IP | 192.168.1.5 |
| Attacker IP | 192.168.1.7 |
| Protocol | TCP |
| Destination Port | 4444 |
| Traffic Type | Reverse Shell |
| Packet Type | PSH/ACK |
| Evidence | TCP Stream |

---

# Evidence Collected

- PCAP File
- TCP Handshake
- TCP Stream
- PSH/ACK Packets
- Wireshark Screenshots

---

# SOC Tier-1 Assessment

The investigation confirmed that the Ubuntu workstation established an outbound TCP connection to the Kali Linux system over port 4444. Continuous PSH/ACK packets and TCP Stream analysis verified interactive command execution consistent with reverse shell activity.

The activity represents a simulated attack conducted within an isolated lab environment for educational purposes.

---

# Recommendations

- Block unauthorized outbound connections.
- Restrict unnecessary TCP ports using firewall rules.
- Deploy Endpoint Detection and Response (EDR).
- Monitor outbound beaconing and shell traffic.
- Enable IDS/IPS signatures for reverse shell detection.
- Investigate similar outbound connections across the network.

---

# Lessons Learned

- Identify reverse shell traffic using TCP filters.
- Verify TCP handshakes before analysis.
- Interpret PSH/ACK packets carrying application data.
- Use Follow TCP Stream to reconstruct attacker activity.
- Collect and document network-based IOCs.
- Follow the Tier-1 SOC investigation workflow.

---

# Conclusion

This lab successfully simulated a reverse shell attack from Ubuntu (192.168.1.5) to Kali Linux (192.168.1.7). The investigation demonstrated how a SOC Analyst validates suspicious outbound connections, reconstructs attacker activity using Wireshark, collects evidence, and prepares the incident for escalation. The exercise provides practical experience in detecting one of the most common techniques used by attackers after initial system compromise.

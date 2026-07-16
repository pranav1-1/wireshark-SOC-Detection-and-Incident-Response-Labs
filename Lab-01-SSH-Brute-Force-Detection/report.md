# SSH Brute Force Detection Investigation Report

## Incident Summary

A SIEM alert indicated repeated SSH login attempts against an internal Ubuntu server.

---

## Investigation Steps

1. Verified SSH service availability.
2. Started Wireshark capture.
3. Generated SSH brute-force traffic using Hydra.
4. Captured network packets.
5. Applied SSH display filters.
6. Identified attacker and victim IP addresses.
7. Examined TCP Port 22 traffic.
8. Reviewed authentication logs.
9. Collected Indicators of Compromise.
10. Assessed incident severity.

---

## Findings

Attacker IP:
192.168.1.7

Target Server:
192.168.1.5

Protocol:
SSH

Destination Port:
22

Attack Type:
SSH Brute Force

Authentication:
Verified using Linux authentication logs.

---

## Indicators of Compromise

- Multiple SSH sessions
- Repeated login attempts
- Source IP
- Destination IP
- SSH traffic on TCP Port 22

---

## Severity

Medium

(High if successful authentication is observed.)

---

## Tier-1 Analyst Decision

The activity is consistent with an SSH brute-force attack.

Document the findings and escalate if authentication is successful or organizational policy requires additional containment actions.

---

## MITRE ATT&CK

T1110 – Brute Force

---

## Conclusion

The investigation confirmed repeated SSH connection attempts targeting the Ubuntu server. Network traffic and authentication logs provided sufficient evidence to identify a brute-force attack and support incident documentation.

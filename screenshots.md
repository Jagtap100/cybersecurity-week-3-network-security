# WEEK 3 – ADVANCED CYBERSECURITY PRACTICAL
# SCREENSHOTS AND EVIDENCE

## TASK 7 – NETWORK DISCOVERY & BASIC NMAP SCANNING

### Screenshot 1 – Network Configuration

- IP Address
- Subnet
- Default Gateway
- Lab VM IP Addresses

### Screenshot 2 – Nmap Host Discovery

Command:

`bash
nmap -sn <lab-network>

Screenshot should show:

Nmap command

Active/live hosts

IP addresses discovered


Screenshot 3 – Basic Nmap Scan

Command:

nmap <target-ip>

Screenshot should show:

Target IP

Nmap command

Open ports

Port states

Services


Screenshot 4 – Discovered Ports and Services

Port Protocol State Service

Actual Result Actual Result Actual Result Actual Result



---

TASK 8 – ADVANCED NMAP SECURITY ASSESSMENT

Screenshot 1 – Nmap Version

nmap --version

Screenshot 2 – Service and Version Detection

nmap -sV <target-ip>

Screenshot 3 – Operating System Detection

sudo nmap -O <target-ip>

Screenshot 4 – TCP SYN Scan

sudo nmap -sS <target-ip>

Screenshot 5 – UDP Scan

sudo nmap -sU --top-ports 20 <target-ip>

Screenshot 6 – NSE Vulnerability Scan

nmap --script vuln <target-ip>

Screenshot 7 – Saved Service Scan

nmap -sV <target-ip> -oN service_scan.txt

nmap -sV <target-ip> -oX service_scan.xml

Advanced Nmap Results

IP Address Port Protocol Service Version Risk Observation

Actual Result Actual Result Actual Result Actual Result Actual Result Actual Result Actual Result



---

TASK 9 – WIRESHARK NETWORK TRAFFIC CAPTURE

Screenshot 1 – Wireshark Interface

Show the selected authorized lab network interface.

Screenshot 2 – Traffic Capture

Capture traffic for approximately 5–10 minutes.

Save as:

traffic_capture.pcapng

Screenshot 3 – DNS

Filter:

dns

Show DNS query and response.

Screenshot 4 – TCP

Filter:

tcp

Show TCP connection details.

Screenshot 5 – UDP

Filter:

udp

Show UDP packet details.

Screenshot 6 – ICMP

Filter:

icmp

Show ICMP Echo Request and Echo Reply.

Screenshot 7 – ARP

Filter:

arp

Show ARP Request and ARP Reply.

Screenshot 8 – HTTP

Filter:

http

Show HTTP traffic if present.

Special Wireshark Filters

tcp.flags.syn == 1

tcp.flags.syn == 1 && tcp.flags.ack == 0

tcp.flags.reset == 1

dns.flags.response == 0

Packet Observation Table

Timestamp Source IP Destination IP Protocol Source Port Destination Port Packet Information Security Observation

Actual Result Actual Result Actual Result Actual Result Actual Result Actual Result Actual Result Actual Result



---

TASK 10 – NMAP + WIRESHARK INVESTIGATION

Screenshot 1 – Nmap Scan

nmap -sS <target-ip>

Screenshot 2 – SYN Packets

tcp.flags.syn == 1 && tcp.flags.ack == 0

Screenshot 3 – SYN/ACK Packets

tcp.flags.syn == 1 && tcp.flags.ack == 1

Screenshot 4 – RST Packets

tcp.flags.reset == 1

Screenshot 5 – Target Port

tcp.port == 80

Replace 80 with the actual port being investigated.

Packet Evidence

Packet No. Source IP Destination IP Source Port Destination Port TCP Flags Observation

Actual Result Actual Result Actual Result Actual Result Actual Result Actual Result Actual Result


Nmap and Wireshark Comparison

Nmap Result Wireshark Evidence Interpretation

Port detected open SYN followed by SYN/ACK Target responded positively
Port detected closed SYN followed by RST Target rejected connection
No expected response No SYN/ACK/RST response Possible filtering, firewall or packet loss



---

TASK 11 – ADVANCED NETWORK TRAFFIC INVESTIGATION

Screenshot 1 – Conversations

Open:

Statistics → Conversations

Check IPv4 and TCP conversations.

Screenshot 2 – Top Communication Hosts

Identify:

Most active source IP

Most active destination IP

Number of packets

Communication between hosts


Screenshot 3 – Protocol Identification

tcp

udp

dns

http

Screenshot 4 – DNS Investigation

dns

Investigate:

DNS queries

DNS responses

Requested domains

Query types

Source and destination IPs


Screenshot 5 – TCP Investigation

tcp

Investigate:

TCP connections

SYN packets

SYN/ACK packets

RST packets
Repeated connection attempts


Screenshot 6 – Suspicious Activity

Look for:

Repeated connection attempts

Unusual ports

Unexpected protocols

Abnormal DNS requests

Large amounts of traffic

Unexpected systems


Traffic Investigation Table

Source IP Destination IP Protocol Port Traffic Pattern Observation

Actual Result Actual Result Actual Result Actual Result Actual Result Actual Result



---

TASK 12 – VULNERABILITY ASSESSMENT

Objective

Identify security weaknesses using information collected during Tasks 7–11.

At least 5 security findings are required.

Each finding should include:

Security Finding

Evidence/Observation

Severity

Reason

Recommendation


Finding 1

Security Finding:
[Actual finding]

Evidence/Observation:
[Actual evidence from Nmap/Wireshark]

Severity:
[Actual Severity]

Reason:
[Reason]

Recommendation:
[Recommendation]

Finding 2

Security Finding:
[Actual finding]

Evidence/Observation:
[Actual evidence from Nmap/Wireshark]

Severity:
[Actual Severity]

Reason:
[Reason]

Recommendation:
[Recommendation]

Finding 3

Security Finding:
[Actual finding]

Evidence/Observation:
[Actual evidence from Nmap/Wireshark]

Severity:
[Actual Severity]

Reason:
[Reason]

Recommendation:
[Recommendation]

Finding 4

Security Finding:
[Actual finding]

Evidence/Observation:
[Actual evidence from Nmap/Wireshark]

Severity:
[Actual Severity]

Reason:
[Reason]

Recommendation:
[Recommendation]

Finding 5

Security Finding:
[Actual finding]

Evidence/Observation:
[Actual evidence from Nmap/Wireshark]

Severity:
[Actual Severity]

Reason:
[Reason]

Recommendation:
[Recommendation]

Vulnerability Assessment Table

S.No. Security Finding Evidence/Observation Severity Reason Recommendation

1 Actual Finding Actual Evidence Actual Severity Actual Reason Actual Recommendation
2 Actual Finding Actual Evidence Actual Severity Actual Reason Actual Recommendation
3 Actual Finding Actual Evidence Actual Severity Actual Reason Actual Recommendation
4 Actual Finding Actual Evidence Actual Severity Actual Reason Actual Recommendation
5 Actual Finding Actual Evidence Actual Severity Actual Reason Actual Recommendation



---

TASK 13 – SECURITY HARDENING & BEFORE/AFTER TESTING

Before Hardening

Run a baseline Nmap scan:

nmap <target-ip>

Record:

Open ports

Running services

Relevant versions

Security weaknesses


Screenshot – Before Hardening

Add the baseline Nmap screenshot.

Security Improvement 1

Action:
[Actual hardening action]

Reason:
[Reason]

Screenshot:
Add screenshot.

Security Improvement 2

Action:
[Actual hardening action]

Reason:
[Reason]

Screenshot:
Add screenshot.

Security Improvement 3

Action:
[Actual hardening action]

Reason:
[Reason]

Screenshot:
Add screenshot.

Examples of Hardening Actions

Disable unnecessary services

Close unused ports

Tighten firewall policy

Restrict network exposure

Patch outdated packages

Improve security configuration


After Hardening

Run Nmap again:

nmap <target-ip>

Screenshot – After Hardening

Add the after-hardening Nmap screenshot.

Before vs After Table

Finding Before Action Taken After

Actual Finding Actual State Actual Action Actual State
Actual Finding Actual State Actual Action Actual State
Actual Finding Actual State Actual Action Actual State


Attack Surface Comparison

Before hardening:

Open ports: [Actual Number]

Exposed services: [Actual Number]


After hardening:

Open ports: [Actual Number]

Exposed services: [Actual Number]


Verification

Confirm using the after-hardening Nmap scan that the previously identified issues were addressed.


---

TASK 14 – FINAL MINI SECURITY ASSESSMENT

Introduction

This assessment combines:

Network discovery

Traffic analysis

Vulnerability identification

Security hardening

Before/after verification


The assessment is performed in an authorized lab environment.


---

1. NETWORK DISCOVERY

Objective

Identify live devices and determine which services each device exposes.

Methodology

A host discovery scan was performed using Nmap, followed by a detailed port/service scan.

Host Discovery
nmap -sn <network-range>

Full Port and Service Scan

nmap -sS -sV -p- <target-ip>

Devices Identified

IP Address Hostname/OS Device Type

Actual Result Actual Result Actual Result
Actual Result Actual Result Actual Result


Services Exposed

Host Port Service Version

Actual Result Actual Result Actual Result Actual Result
Actual Result Actual Result Actual Result Actual Result


Evidence

Add Nmap screenshot here.


---

2. TRAFFIC ANALYSIS

Objective

Capture and analyze network traffic to understand protocols and communication patterns.

Methodology

Traffic was captured using Wireshark over the defined observation period.

Observed Protocols

List protocols actually seen in the capture.

Examples:

HTTP

DNS

ARP

SSH

FTP

SMB

Telnet


Plaintext Protocols

Document any observed unencrypted/plaintext protocols.

Examples:

HTTP

Telnet

FTP


Communication Patterns

Describe:

Which hosts communicate

Source IP

Destination IP

Ports used

Repeated connections

Broadcast traffic

Any unusual communication


Traffic Evidence

Add relevant Wireshark screenshots here.


---

3. SECURITY ASSESSMENT

Objective

Consolidate the Nmap and Wireshark findings into a list of security issues.

Major Findings

Finding 1

Issue:
[Actual finding]

Evidence:
[Actual Nmap/Wireshark evidence]

Risk:
[High / Medium / Low]

Potential Impact:
[Actual impact]

Finding 2

Issue:
[Actual finding]

Evidence:
[Actual Nmap/Wireshark evidence]

Risk:
[High / Medium / Low]

Potential Impact:
[Actual impact]

Finding 3

Issue:
[Actual finding]

Evidence:
[Actual Nmap/Wireshark evidence]

Risk:
[High / Medium / Low]

Potential Impact:
[Actual impact]

Finding 4

Issue:
[Actual finding]

Evidence:
[Actual Nmap/Wireshark evidence]

Risk:
[High / Medium / Low]

Potential Impact:
[Actual impact]

Finding 5

Issue:
[Actual finding]

Evidence:
[Actual Nmap/Wireshark evidence]

Risk:
[High / Medium / Low]

Potential Impact:
[Actual impact]

Evidence References

For each finding, reference:

Nmap scan output

Wireshark screenshot

Packet number

Service/version information



---

4. HARDENING

Objective

Apply remediation to the identified security findings and verify improvement.

Security Improvements Implemented

1. [Actual hardening action]


2. [Actual hardening action]


3. [Actual hardening action]



Before vs After Comparison

Finding Before Action Taken After

Actual Finding Actual State Actual Action Actual State
Actual Finding Actual State Actual Action Actual State
Actual Finding Actual State Actual Action Actual State


Attack Surface

Before hardening:

Open ports: [Actual Number]


After hardening:

Open ports: [Actual Number]


Verification

The after-hardening Nmap scan was used to verify whether the previously identified issues were addressed.

Add before and after screenshots here.


---

5. FINAL RECOMMENDATIONS

Recommendation 1 – Network Segmentation

Separate critical servers, database systems and management interfaces from general workstation traffic using network segmentation such as VLANs.

Recommendation 2 – Encrypted Protocols

Disable plaintext protocols where possible and use encrypted alternatives such as:

SSH

HTTPS

SFTP


Recommendation 3 – Regular Patch Management

Maintain a regular schedule for checking and applying security updates to operating systems and services.

Recommendation 4 – Centralized Logging and Monitoring

Use centralized logging and monitoring to detect suspicious activity such as:

Repeated failed logins

Port scans

Other unusual network activity


Recommendation 5 – Least-Privilege Firewall Policy

Configure firewall rules to allow only the ports and services that are required.


---

FINAL CONCLUSION

This assessment demonstrates a complete security lifecycle:

1. Network discovery


2. Traffic analysis


3. Risk-based security findings


4. Security remediation


5. Before/after verification



The assessment demonstrates the importance of identifying exposed services, analyzing network traffic, addressing security weaknesses and verifying the effectiveness of security hardening.

# Cybersecurity Week 3 – Network Security

## Project Title

Advanced Cybersecurity Practical – Network Security Assessment

## Objective

The objective of this project is to perform network discovery,
advanced Nmap security assessment, Wireshark network traffic analysis,
Nmap and Wireshark investigation, vulnerability assessment, security
hardening, and final security assessment in an authorized laboratory
environment.

## Lab Environment

- Operating System: Kali Linux
- Nmap Version: 7.95
- Target IP Address: 192.168.58.130
- Environment: Authorized cybersecurity laboratory
- Virtualization: VMware environment
- Network Assessment: Internal laboratory network

All security testing was performed only on authorized laboratory
systems.

## Tools Used

- Nmap
- Wireshark
- Kali Linux
- VMware
- GitHub

## Tasks Completed

### Task 7 – Network Discovery & Basic Nmap Scanning

Network configuration was examined using Linux networking commands.

Host discovery was performed using Nmap.

The lab target was identified and basic port scanning was performed.

The assessment focused on identifying active hosts, open ports,
protocols, and services.

### Task 8 – Advanced Nmap Security Assessment

The following Nmap techniques were performed:

- Service and version detection
- Operating system detection
- TCP SYN scanning
- Top-20 UDP port scanning
- Nmap NSE vulnerability script scanning
- Security analysis of exposed services

#### Service and Version Detection

Target:

192.168.58.130

Observed services included:

| Port | Protocol | State | Service | Version |
|---|---|---|---|---|
| 80 | TCP | Open | HTTP | Apache httpd 2.4.68 (Debian) |
| 9876 | TCP | Open | HTTP | Apache httpd 2.4.68 (Debian) |

The operating system was identified as Linux.

#### Full TCP Scan

A full TCP SYN and service/version scan was also performed.

Observed open TCP ports:

| Port | Protocol | Service | Version |
|---|---|---|---|
| 22 | TCP | SSH | OpenSSH 10.2p1 Debian 3 |
| 80 | TCP | HTTP | Apache httpd 2.4.68 (Debian) |
| 8834 | TCP | HTTPS/SSL related service | Nessus XML-RPC suspected |
| 9876 | TCP | HTTP | Apache httpd 2.4.68 (Debian) |

Nmap did not completely identify the service on port 8834, although
the response contained information indicating a Nessus web service.

#### UDP Scan

A top-20 UDP scan was performed.

The displayed UDP ports in the scan were reported as closed.

#### NSE Vulnerability Scan

The Nmap vulnerability script scan was performed against the
authorized target.

The following observations were recorded:

- /server-status/ was reported as a potentially interesting folder.
- No DOM-based XSS vulnerability was identified.
- No CSRF vulnerability was identified.
- No stored XSS vulnerability was identified.

These results represent observations from the Nmap scan and do not
automatically prove that the system is vulnerable.

## Task 9 – Wireshark Network Traffic Capture

Network traffic was captured and analyzed using Wireshark.

The following protocols were investigated:

- DNS
- TCP
- UDP
- ICMP
- ARP
- HTTP

Wireshark filters were used to examine protocol-specific traffic,
TCP connection attempts, DNS queries, and other network activity.

Important packet information such as source IP, destination IP,
protocol, ports, TCP flags, and packet details was examined.

## Task 10 – Nmap + Wireshark Investigation

The Nmap scan was correlated with Wireshark packet evidence.

Target IP:

192.168.58.130

Nmap identified:

- 80/tcp – Open – HTTP
- 9876/tcp – Open – HTTP

Wireshark captured TCP SYN/ACK packets during the investigation.

Relevant packet numbers documented in the practical were:

- Packet 248
- Packet 249

A TCP SYN/ACK response is consistent with a target responding to a
TCP connection attempt and therefore with an open TCP port.

The packet-to-port mapping should be verified before assigning
packet 248 or 249 to a specific port.

## Task 11 – Advanced Network Traffic Investigation

Wireshark traffic was investigated using communication and protocol
analysis.

The investigation included:
- Top communication hosts
- Active source and destination systems
- TCP communication
- DNS queries and responses
- HTTPS/TLS traffic
- ARP activity
- Packet and conversation analysis
- Repeated connection attempts
- Unusual destination ports
- Unexpected communication patterns

The traffic screenshots show normal TCP/TLS, DNS and ARP communication
as well as other network traffic generated during the observation
period.

## Task 12 – Vulnerability Assessment

The assessment identified security-relevant observations from Nmap
and Wireshark evidence.

### Finding 1 – Multiple Exposed TCP Services

Evidence:

The full Nmap scan identified TCP ports 22, 80, 8834 and 9876 as open.

Impact:

Every exposed service increases the network attack surface and should
be reviewed to determine whether it is required.

Recommendation:

Restrict or disable services that are not required and apply
appropriate firewall rules.

### Finding 2 – HTTP Service Exposed

Evidence:

TCP port 80 was identified as an Apache HTTP service.

Impact:

HTTP traffic is not encrypted at the application layer and may expose
information depending on the application and data being transmitted.

Recommendation:

Use HTTPS/TLS where appropriate and restrict unnecessary access.

### Finding 3 – Additional HTTP Service on Port 9876

Evidence:

TCP port 9876 was identified as Apache HTTP.

Impact:

An additional web service creates another exposed application/service
that should be reviewed and secured.

Recommendation:

Confirm whether the service is required and restrict access if it
does not need broad network exposure.

### Finding 4 – Nessus-Related Service on Port 8834

Evidence:

Nmap identified port 8834 as ssl/nessus-xmlrpc? and returned
information identifying a Nessus-related web response.

Impact:

An exposed management/security service should be restricted to
authorized users and networks.

Recommendation:

Restrict access using firewall/network controls and maintain the
service with appropriate security updates.

### Finding 5 – Potentially Interesting /server-status Directory

Evidence:

The Nmap NSE vulnerability scan reported /server-status/ as a
potentially interesting folder.

Impact:

Server-status information may reveal useful operational or server
information if unnecessarily exposed.

Recommendation:

Restrict access to server-status functionality to authorized
administrators or disable it when not required.

> Note: The above findings are security observations based on the
> practical evidence. An open port or an Nmap informational result
> does not by itself prove a confirmed vulnerability.

## Security Improvements

Security hardening activities focused on reducing unnecessary
exposure and improving service security.

Recommended/implemented security controls include:

- Review unnecessary open ports.
- Restrict exposed services using firewall rules.
- Restrict administrative services to authorized networks.
- Keep Apache and SSH software updated.
- Use HTTPS/TLS for web services where appropriate.
- Restrict access to server-status functionality.
- Disable unnecessary services when they are not required.
- Re-scan the system after security changes.

## Before/After Results

### Before Hardening

The full Nmap assessment identified the following exposed TCP ports:

| Port | Service |
|---|---|
| 22/tcp | SSH |
| 80/tcp | HTTP |
| 8834/tcp | Nessus-related SSL service |
| 9876/tcp | HTTP |

Total observed open TCP ports: 4

### After Hardening

The system should be re-scanned after the applied hardening changes.

| Port/Service | Before | Action | After |
|---|---|---|---|
| SSH – 22/tcp | Open | Restrict access if required | [Actual result] |
| HTTP – 80/tcp | Open | Secure/restrict service | [Actual result] |
| Nessus – 8834/tcp | Open | Restrict management access | [Actual result] |
| HTTP – 9876/tcp | Open | Review/restrict if unnecessary | [Actual result] |

The final after-hardening values should be based on the actual
post-hardening Nmap scan.

## Key Findings
The network assessment identified multiple exposed TCP services on
192.168.58.130.

The advanced Nmap scan identified SSH, Apache HTTP services, and a
Nessus-related service.

Wireshark analysis provided packet-level visibility into TCP, DNS,
ARP, HTTP and other network communication.

The Nmap and Wireshark investigation demonstrated how TCP SYN and
SYN/ACK packets can be used to understand connection attempts and
validate port behavior.

The NSE scan reported /server-status/ as potentially interesting,
while the tested DOM-based XSS, CSRF, and stored-XSS checks did not
identify vulnerabilities.

## Evidence

The project contains evidence for:

- Network configuration
- Nmap host discovery
- Basic Nmap scan
- Advanced Nmap scan
- Service/version detection
- OS detection
- UDP scan
- NSE vulnerability scan
- Wireshark traffic capture
- DNS analysis
- TCP analysis
- ARP analysis
- Nmap + Wireshark investigation
- Vulnerability assessment
- Security hardening
- Before/after testing

## Conclusion

This project provided practical experience in network discovery,
Nmap-based security assessment, Wireshark packet analysis,
vulnerability assessment, and security hardening.

The assessment identified exposed services and analyzed network
communication in an authorized laboratory environment.

The combination of Nmap results and Wireshark evidence helped connect
network-level port states with actual TCP packet behavior.

The project also demonstrated the importance of reviewing exposed
services, restricting unnecessary access, protecting web services,
and verifying security changes through before-and-after testing.

# Wireshark Network Traffic Capture

## Objective

The objective of this practical is to capture and analyze network
traffic using Wireshark.

Wireshark is used to:

- Capture network packets
- Analyze network protocols
- Investigate suspicious communication
- Troubleshoot network issues
- Identify potential security problems

## Network Traffic Capture

1. Open Wireshark.
2. Select the authorized lab network interface.
3. Start packet capture.
4. Generate normal network traffic.
5. Capture traffic for approximately 5–10 minutes.
6. Stop the capture.
7. Save the capture as:

traffic_capture.pcapng

## Generate Normal Traffic

The following activities were performed in the authorized lab:

- Open a website
- Perform a DNS query
- Ping the authorized lab machine
- Connect to an authorized local service

Example DNS command:

nslookup example.com

Example ping command:

ping example.com

## Protocols Analyzed

### DNS

DNS is used to translate domain names into IP addresses.

Wireshark filter:

dns

Information analyzed:

- Timestamp
- Source IP
- Destination IP
- DNS query
- DNS response
- Security observation

### TCP

TCP provides reliable and ordered communication.

Wireshark filter:

tcp

TCP three-way handshake:

SYN → SYN/ACK → ACK

The following information was analyzed:

- Source IP
- Destination IP
- Source port
- Destination port
- TCP flags

### UDP

UDP is a connectionless transport protocol.

Wireshark filter:

udp

Information analyzed:

- Source IP
- Destination IP
- Source port
- Destination port
- Packet information

### ICMP

ICMP is used for network diagnostics and connectivity testing.

Wireshark filter:

icmp

Ping traffic includes:

- Echo Request
- Echo Reply

### ARP

ARP is used to find the MAC address associated with an IP address
on a local IPv4 network.

Wireshark filter:

arp

Information analyzed:

- Sender IP
- Sender MAC
- Target IP
- Target MAC
- ARP request
- ARP reply

### HTTP

HTTP is used for web communication.

Common port:

TCP 80

Wireshark filter:

http

Information analyzed:

- HTTP request
- HTTP response
- Source IP
- Destination IP
- Source port
- Destination port

HTTP traffic may not appear when visiting modern websites because
most websites use HTTPS.

## Wireshark Filters

DNS:

dns

TCP:

tcp

UDP:

udp

ICMP:

icmp

ARP:

arp

HTTP:

http

TCP SYN:

tcp.flags.syn == 1

Initial TCP SYN:

tcp.flags.syn == 1 && tcp.flags.ack == 0

TCP Reset:

tcp.flags.reset == 1

DNS Queries:

dns.flags.response == 0

## Packet Information

For important packets, record:

- Timestamp
- Source IP
- Destination IP
- Protocol
- Source Port
- Destination Port
- Packet Information
- Security Observation

## Important Screenshots

The following screenshots should be included:

1. DNS Query
2. DNS Response
3. TCP SYN
4. TCP SYN-ACK
5. TCP ACK
6. UDP Packet
7. ICMP Echo Request
8. ICMP Echo Reply
9. ARP Request
10. ARP Reply
11. HTTP Packet, if present

## Nmap + Wireshark Investigation

The objective was to run an Nmap scan and capture the generated
traffic using Wireshark.

Nmap command:

nmap -sS <target-ip>

The Wireshark capture was started before the Nmap scan and stopped
after the scan.

### TCP Packet Analysis

SYN → SYN/ACK generally indicates an open port.

SYN → RST generally indicates a closed port.

No expected response may indicate filtering, firewall behavior,
or packet loss.

### Filters Used

TCP SYN:

tcp.flags.syn == 1 && tcp.flags.ack == 0

TCP SYN-ACK:

tcp.flags.syn == 1 && tcp.flags.ack == 1

TCP RST:

tcp.flags.reset == 1

Target IP:

ip.addr == 192.168.58.130

Port:

tcp.port == 80

## Nmap and Wireshark Comparison

| Nmap Result | Wireshark Evidence | Interpretation |
|---|---|---|
| Open port | SYN → SYN/ACK | Port responded to connection attempt |
| Closed port | SYN → RST | Port rejected connection |
| No response | No expected response | Possible filtering/firewall |

## Documented Lab Result

Target IP:

192.168.58.130

Nmap detected:

- 80/tcp – Open – HTTP
- 9876/tcp – Open – sd

Documented Wireshark packet numbers:

- 248
- 249
  The packet numbers should be matched with the corresponding ports
before assigning them as evidence.

## Conclusion

This practical demonstrated how Wireshark can be used to capture and
analyze network traffic.

DNS, TCP, UDP, ICMP, ARP and HTTP traffic were studied using Wireshark
filters.

The Nmap and Wireshark investigation demonstrated how TCP SYN,
SYN-ACK and RST packets can be used to understand network
communication and port states.

The practical improved understanding of network traffic analysis and
security investigation in an authorized laboratory environment.

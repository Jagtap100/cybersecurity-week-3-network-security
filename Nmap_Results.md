# Nmap Results – Week 3 Network Security

## 1. Assessment Information

- Project: Cybersecurity Week 3 – Network Security
- Tool: Nmap
- Nmap Version: 7.95
- Target IP: 192.168.58.130
- Environment: Authorized Cybersecurity Laboratory

## 2. Host Discovery

Host discovery was performed using Nmap to identify active systems
within the authorized laboratory network.

### Command Used

nmap -sn <lab-network>

The practical identified the target system:

192.168.58.130

## 3. Basic Nmap Scan

### Command Used

nmap 192.168.58.130

### Result

The target was identified as up.

Open TCP ports observed:

| Port | Protocol | State | Service |
|------|----------|-------|---------|
| 80 | TCP | Open | HTTP |
| 9876 | TCP | Open | sd |

## 4. Service and Version Detection

### Command Used

nmap -sV 192.168.58.130

### Result

The scan identified the following services:

| Port | Protocol | State | Service | Version |
|------|----------|-------|---------|---------|
| 22 | TCP | Open | SSH | OpenSSH 10.2p1 Debian 3 |
| 80 | TCP | Open | HTTP | Apache httpd 2.4.68 (Debian) |
| 8834 | TCP | Open | HTTPS/SSL-related | Nessus XML-RPC suspected |
| 9876 | TCP | Open | HTTP | Apache httpd 2.4.68 (Debian) |

Port 8834 was not completely identified by Nmap; the result indicated
a Nessus-related SSL/XML-RPC service.

## 5. Operating System Detection

### Command Used

sudo nmap -O 192.168.58.130

### Result

Nmap estimated the target operating system as Linux.

OS detection is an estimate and depends on the available network
responses and Nmap detection techniques.

## 6. TCP SYN Scan

### Command Used

sudo nmap -sS 192.168.58.130

### Result

The TCP SYN scan identified open TCP services on the target,
including:

- 22/tcp – SSH
- 80/tcp – HTTP
- 8834/tcp – Nessus-related SSL service
- 9876/tcp – HTTP

## 7. UDP Scan

### Command Used

sudo nmap -sU --top-ports 20 192.168.58.130

### Result

The top-20 UDP scan showed the displayed UDP ports as closed.

No open UDP service was identified in the documented top-20 UDP scan.

## 8. NSE Vulnerability Scan

### Command Used

nmap --script vuln 192.168.58.130

### Observations

The NSE scan reported:

- /server-status/ as a potentially interesting folder.
- DOM-based XSS was not identified.
- CSRF vulnerabilities were not identified.
- Stored XSS vulnerabilities were not identified.

The /server-status/ result should be reviewed as a
security-relevant observation.

An Nmap NSE result or an open port alone does not automatically prove
a confirmed vulnerability.

## 9. Security Observations

### Port 22/tcp – SSH

SSH provides remote administration access.

Security considerations:

- Use strong authentication.
- Prefer SSH keys where appropriate.
- Disable unnecessary accounts.
- Keep SSH software updated.
- Restrict access using firewall/network controls.
- Monitor authentication logs.

### Port 80/tcp – HTTP

Apache HTTP service was detected.

Security considerations:

- Keep the web server updated.
- Use HTTPS/TLS where appropriate.
- Restrict unnecessary network access.
- Disable unnecessary web-server features.
- Monitor web-server logs.

### Port 8834/tcp

Nmap indicated a Nessus-related SSL/XML-RPC service.

Security consideration:

Access to management/security services should be restricted to
authorized users and networks.

### Port 9876/tcp

Apache HTTP service was detected on the additional port.

The purpose of this service should be reviewed and access should be
restricted if broad network exposure is unnecessary.

### /server-status/

Nmap reported /server-status/ as potentially interesting.

Access to server-status functionality should be restricted to
authorized administrators or disabled when it is not required.

## 10. Nmap Results Summary

| Port | Protocol | Service | Version | Security Observation |
|------|----------|---------|---------|----------------------|
| 22 | TCP | SSH | OpenSSH 10.2p1 Debian 3 | Remote administration exposure |
| 80 | TCP | HTTP | Apache httpd 2.4.68 (Debian) | Web service exposed |
| 8834 | TCP | SSL/Nessus-related | Nessus XML-RPC suspected | Management service exposure |
| 9876 | TCP | HTTP | Apache httpd 2.4.68 (Debian) | Additional web service exposed |

## 11. Conclusion

The Nmap assessment identified the authorized laboratory target
192.168.58.130 and identified multiple exposed TCP services.

Service and version detection identified OpenSSH and Apache HTTP
services. OS detection estimated the system as Linux. The top-20 UDP
scan showed the documented UDP ports as closed.

The NSE vulnerability scan reported /server-status/ as potentially
interesting, while the documented XSS and CSRF checks did not identify
the tested vulnerabilities.

The results were reviewed to understand exposed services, potential
security concerns, and appropriate security controls.

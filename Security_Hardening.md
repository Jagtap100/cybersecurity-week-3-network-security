# TASK 13 – SECURITY HARDENING & BEFORE/AFTER TESTING

## 1. Objective

The objective of this task is to identify security weaknesses present in an authorized lab environment, apply security hardening measures to fix them, and demonstrate the improvement in security posture through a structured before-and-after comparison using network scanning tools such as Nmap.

---

## 2. Introduction to Security Hardening

Security hardening is the process of reducing the attack surface of a system.

A system's attack surface generally increases with:

- Running services
- Open network ports
- Installed software packages
- Permissive configurations

Security hardening is a defensive and proactive security practice.

It follows the principles of:

- Confidentiality
- Integrity
- Availability
- Principle of Least Privilege

The hardening process can be viewed as a continuous cycle:

Assess → Harden → Verify → Monitor → Reassess

---

## 3. Importance of Before/After Testing

Simply applying a configuration change is not sufficient proof that security has improved.

Before/after testing provides objective and reproducible evidence by:

1. Capturing the system state before remediation.
2. Applying security hardening measures.
3. Scanning the system again after remediation.
4. Comparing the results.

Before/after testing helps to:

- Provide verifiable proof of remediation.
- Detect unintended side effects.
- Build a documented audit trail.
- Validate that security fixes actually worked.

---

## 4. Role of Nmap in Security Assessment

Nmap (Network Mapper) is an open-source utility used for network discovery and security auditing.

Nmap can help identify:

- Online hosts
- Open ports
- Closed ports
- Filtered ports
- Running services
- Service versions

### Common Nmap Scan Types

#### TCP SYN Scan

`bash
sudo nmap -sS [TARGET-IP]

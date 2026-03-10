# Quickstart-CTF-Windows-Penetration-Test

## Overview

This project documents a complete penetration testing simulation against a deliberately vulnerable Windows machine as the final career simulation for the Quickstart Cybersecurity Bootcamp. The objective was to perform reconnaissance, vulnerability discovery, exploitation, privilege escalation, and sensitive data recovery in a controlled, isolated lab environment using Kali Linux tools.

All activities were conducted ethically within VirtualBox using a NAT network — no unauthorized systems were targeted.

The project demonstrates core penetration testing skills: network setup, scanning, exploitation with Metasploit, post-exploitation, and professional reporting.

---

## Environment & Architecture

Isolated lab deployed in Oracle VirtualBox with no external internet exposure.

**Systems included:**

- Attacker: Kali Linux CTF VM
- Target: Windows CTF VM (vulnerable Windows system)
- Network: Custom NAT Network named "Quickstart" (10.0.2.0/24, DHCP enabled)

Kali acted as the attacking platform; the Windows target hosted exploitable services.

---

## Project Objectives

- Configure an isolated NAT network in VirtualBox
- Discover the target IP and enumerate open services/versions
- Identify exploitable vulnerabilities (primarily MS17-010 / EternalBlue)
- Gain administrative (SYSTEM) access via Metasploit
- Locate and exfiltrate hidden sensitive files:
  - hoot.txt (the "Flag")
  - hashbrowns1.txt
  - hide.jpeg
- Document the entire process with screenshots and security recommendations

---

## Tools & Technologies

- **Oracle VirtualBox** (NAT networking)
- **Kali Linux** (attacking platform)
- **Nmap** (host discovery, port scanning, vulnerability scripting)
- **Metasploit Framework** (exploit execution, Meterpreter shell)
- **Meterpreter** (post-exploitation commands)
- Standard Linux utilities (find, type, strings, etc.)

---

## Key Tasks Completed

- Created and verified NAT network "Quickstart" (10.0.2.0/24)
- Identified target IP using nmap ping sweep
- Performed comprehensive port and vulnerability scanning
- Exploited MS17-010 (EternalBlue) to obtain SYSTEM-level Meterpreter session
- Searched filesystem and recovered the three required files
- Displayed contents of hoot.txt (flag), hashbrowns1.txt, and analyzed hide.jpeg
- Captured evidence screenshots at each major stage

---

## Exploitation & Findings Summary

- **Target IP**: 10.0.2.4 (example; actual may vary)
- **Key Vulnerability**: SMBv1 MS17-010 (EternalBlue) on port 445
- **Exploit Used**: `exploit/windows/smb/ms17_010_eternalblue` in Metasploit
- **Access Achieved**: NT AUTHORITY\SYSTEM privileges
- **Files Recovered**:
  - hoot.txt → Main flag file (e.g., "Congratulations! You have pwned the box.")
  - hashbrowns1.txt → Additional sensitive data (possibly containing a hash)
  - hide.jpeg → Hidden/embedded content or steganography example

Detailed walkthrough, commands, and outputs are available in the presentation slides and demo recording.

---

## Security Recommendations

- Immediately apply MS17-010 patch (or disable SMBv1 entirely)
- Disable unnecessary services and close unused ports (especially 445)
- Implement strong firewall rules to block inbound SMB unless required
- Enforce credential protection and avoid legacy protocols
- Regularly scan internal networks for vulnerable systems
- Use application whitelisting and endpoint detection/response (EDR) tools
- Conduct periodic penetration testing and vulnerability assessments

---

## Screenshots & Evidence

Supporting screenshots (network setup, nmap results, Metasploit exploit, file contents, etc.) are available in the `screenshots/` directory.

Presentation slides and demo recording are submitted separately via the bootcamp dashboard.

---

## Disclaimer

This project was completed in a fully isolated, educational lab environment for training and portfolio purposes only. No real production systems, networks, or sensitive data were accessed or harmed. All activities align with legal and ethical penetration testing guidelines.

# Bootcamp-Final-CTF-Writeup
Final project for Quickstart Cybersecurity Bootcamp – Windows CTF penetration test simulation using Kali Linux and Metasploit
# Quickstart Cybersecurity Bootcamp – Final Career Simulation Project

**Penetration Testing of Windows CTF Target**

**Author:** Alejandro  
**Date:** March 2025  
**Location:** Denver, CO  
**Bootcamp:** Quickstart Cybersecurity  

## Executive Summary

This project demonstrates a full penetration test simulation against a vulnerable Windows machine in a controlled VirtualBox NAT network (10.0.2.0/24). Using Kali Linux tools, I identified vulnerabilities, exploited them to gain SYSTEM-level access, and recovered hidden sensitive files (the "Flag" and others).

**Key Achievements:**
- Set up isolated NAT network in VirtualBox
- Discovered target IP and enumerated services with Nmap
- Identified MS17-010 (EternalBlue) vulnerability
- Exploited via Metasploit to obtain administrative Meterpreter session
- Located and exfiltrated hoot.txt (flag), hashbrowns1.txt, and hide.jpeg

**Important Note:** All activities were performed in a legal, educational lab environment with explicit permission.

## Project Scope & Environment

- **Attacker:** Kali Linux CTF VM
- **Target:** Windows CTF VM
- **Network:** VirtualBox NAT Network – Quickstart (10.0.2.0/24, DHCP enabled)
- **Tools Used:** nmap, Metasploit Framework (msfconsole), Meterpreter

## Step-by-Step Walkthrough

### 1. VirtualBox NAT Network Setup
Created NAT network named "Quickstart" with CIDR 10.0.2.0/24 and DHCP enabled.

![NAT Network Setup](screenshots/1-nat-network.png)

### 2. Target Discovery
- Kali IP: 10.0.2.15
- Target IP discovered via `nmap -sn 10.0.2.0/24` → **10.0.2.4**

![Host Discovery](screenshots/2-nmap-ping-sweep.png)

### 3. Vulnerability Scanning
Full port scan + vuln scripts:

```bash
sudo nmap -sS -sV -p- -T4 --script vuln 10.0.2.4

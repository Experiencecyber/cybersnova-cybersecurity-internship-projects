# Project 1: Network Reconnaissance & Service Enumeration

## Overview

This project involved performing authorized network reconnaissance and service enumeration against `scanme.nmap.org`, an official Nmap practice target.

The objective was to identify the target's availability, open ports, running services, software versions and web technologies.

## Lab Environment

- **Operating System:** Kali Linux
- **Target:** scanme.nmap.org
- **Target IP:** 45.33.32.156
- **Network:** NAT
- **Host IP:** 10.0.2.15

## Tools Used

- **Nmap 7.95:** Port scanning and service/version detection.
- **cURL:** HTTP header inspection.
- **WhatWeb:** Web technology identification.
- **Ping:** Network connectivity testing.

## Methodology and Commands

### 1. Connectivity Testing

```bash
ping -c 4 scanme.nmap.org
```

The target responded successfully with zero packet loss.

### 2. Port Reconnaissance

```bash
nmap -T4 --top-ports 20 scanme.nmap.org
```

The scan identified two open ports:

- Port 22 – SSH
- Port 80 – HTTP

### 3. Service and Version Detection

```bash
nmap -sV -p 22,80 scanme.nmap.org
```

Identified services:

- SSH: OpenSSH 6.6.1p1 Ubuntu
- HTTP: Apache 2.4.7 Ubuntu

### 4. HTTP Header Inspection

```bash
curl -I http://scanme.nmap.org
```

The server returned HTTP 200 OK and disclosed Apache server information.

### 5. Web Technology Identification

```bash
whatweb http://scanme.nmap.org
```

Identified technologies included Apache, Ubuntu Linux and HTML5.

### 6. Operating System Detection

```bash
sudo nmap -O -p 22,80 scanme.nmap.org
```

Nmap indicated that the operating-system result could be unreliable. Therefore, no exact operating system was claimed from this scan.

## Key Findings

- Two open services were identified: SSH and HTTP.
- Service enumeration revealed the software versions running on both ports.
- HTTP headers disclosed web-server information.
- WhatWeb identified technologies associated with the target website.

## Security Recommendations

- Restrict SSH access to trusted sources where appropriate.
- Use strong SSH authentication, preferably key-based authentication.
- Keep Apache, OpenSSH and the operating system updated with supported security releases.
- Disable unnecessary exposed services.
- Monitor SSH and web-server logs for suspicious activity.
- Conduct regular authorized security assessments.

## Learning Outcomes

This exercise strengthened my practical understanding of:

- Network reconnaissance.
- Port scanning and service enumeration.
- Service-version identification.
- HTTP header analysis.
- Web technology fingerprinting.
- Security findings and recommendations.

## Scope and Authorization

Testing was limited to the authorized Nmap practice target and conducted for educational purposes. No exploitation was performed.

**Author:** Anayo Okafor

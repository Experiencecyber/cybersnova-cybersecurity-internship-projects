# Project 2: Web Directory & File Enumeration

## Overview

This project involved performing web directory and file enumeration against the intentionally vulnerable training website `testasp.vulnweb.com`.

The objective was to identify hidden directories, files and potentially exposed web resources, then manually verify selected findings.

## Lab Environment

- **Assessment Platform:** Kali Linux
- **Target:** `http://testasp.vulnweb.com/`
- **Tool:** Gobuster 3.8
- **Wordlist:** `/usr/share/wordlists/dirb/common.txt`

## Tools Used

- Gobuster 3.8 – Directory and file enumeration.
- cURL – Manual verification of HTTP responses.
- Kali Linux – Security assessment environment.

## Methodology and Commands

### 1. Directory Enumeration

The following command was used:

```bash
gobuster dir -u http://testasp.vulnweb.com/ -w /usr/share/wordlists/dirb/common.txt -t 10 -o project2_gobuster.txt
```

The scan processed 4,613 entries and identified several directories and resources.

### 2. Identified Resources

Selected results included:

- `/_vti_cnf/`
- `/aspnet_client/`
- `/avatars/`
- `/cgi-bin/`
- `/HTML/`
- `/images/`
- `/jscripts/`
- `/robots.txt`
- `/templates/`

Several paths returned redirects, while `/cgi-bin/` returned HTTP 403 Forbidden.

### 3. Manual Verification

cURL was used to manually inspect selected responses.

The most significant finding was:

`/_vti_cnf/`

Manual verification returned HTTP 200 OK and exposed FrontPage configuration metadata.

The exposed metadata referenced application resources such as:

- `login.asp`
- `register.asp`
- `search.asp`
- `showthread.asp`
- `showforum.asp`
- `Templatize.asp`

The response also identified the server as Microsoft-IIS/8.5 with ASP.NET.

## Key Finding

**Information Disclosure through Exposed Configuration Metadata**

The publicly accessible configuration metadata revealed information about the application's structure and referenced resources.

This could help an attacker understand the application's architecture and identify areas for further investigation.

Directories returning HTTP 403 Forbidden were not treated as confirmed vulnerabilities because access was denied.

## Security Recommendations

- Restrict access to sensitive configuration files and directories.
- Remove unnecessary configuration and metadata directories from production systems.
- Review IIS and ASP.NET permissions and access controls.
- Remove unnecessary or legacy web components.
- Conduct regular authorized directory and file enumeration during security assessments.

## Learning Outcomes

This exercise strengthened my understanding of:

- Web directory and file enumeration.
- Gobuster usage and wordlist-based discovery.
- HTTP response-code analysis.
- Manual verification using cURL.
- Information disclosure risks.
- Web server security and access controls.

## Scope and Authorization

Testing was conducted against an intentionally vulnerable training website for educational purposes.

**Author:** Anayo Okafor

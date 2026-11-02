# Project 5: OWASP Juice Shop Security Assessment

## Project Overview
This project involved assessing a locally hosted OWASP Juice Shop application to identify common web application security weaknesses and document potential risks and remediation measures.

## Lab Environment
- **Target:** `http://localhost:3000`
- **Operating System:** Kali Linux
- **Tools:** OWASP Juice Shop, cURL, Firefox

## Objectives
- Identify potential security weaknesses in a web application.
- Examine publicly accessible resources and application responses.
- Identify information disclosure issues.
- Document findings and recommend remediation measures.

## Methodology
1. Started the OWASP Juice Shop application in the local lab environment.
2. Accessed the application through a web browser.
3. Inspected application endpoints and HTTP responses.
4. Reviewed accessible files, error responses, and security-related HTTP headers.
5. Documented the findings and proposed recommendations.

## Key Findings

| Finding | Severity |
|---|---|
| Publicly accessible `/ftp/` directory listing | Medium |
| Unauthenticated access to `/ftp/acquisitions.md` | Medium |
| Verbose error response exposing stack traces and internal application details | Low |
| Missing Content Security Policy (CSP) | Informational/Low |
| Missing Referrer-Policy header | Informational/Low |
| Public `/metrics` endpoint exposing application metrics | Low, depending on sensitivity |

## Security Risks
- Publicly accessible files may expose information that should not be available to unauthenticated users.
- Detailed error messages may reveal internal application structure and technology information.
- Missing security headers may reduce the application's protection against certain browser-based attacks.
- Exposed metrics may disclose operational information about the application.

## Recommendations
- Restrict access to sensitive files and remove confidential resources from publicly accessible directories.
- Disable directory listing where it is not required.
- Configure generic error messages and prevent exposure of internal stack traces.
- Implement an appropriate Content Security Policy.
- Configure a suitable Referrer-Policy header.
- Review access to the `/metrics` endpoint and restrict it where necessary.

## Conclusion
The assessment identified several security weaknesses in the locally hosted OWASP Juice Shop application, including information disclosure, directory listing, and missing security headers. The exercise provided practical experience in inspecting web application behaviour, identifying potential vulnerabilities, documenting findings, and recommending remediation measures.

**Tools and Skills:** OWASP Juice Shop, cURL, Firefox, web application assessment, information disclosure analysis, security documentation.

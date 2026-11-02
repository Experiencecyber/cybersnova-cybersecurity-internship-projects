# Project 3: Login Traffic Analysis

## Project Overview
This project involved capturing and analysing HTTP login traffic using Wireshark to understand how login information is transmitted between a client and a web server.

## Lab Environment
- **Target:** `http://testasp.vulnweb.com/login.asp`
- **Operating System:** Kali Linux
- **Tools:** Wireshark, cURL

## Objectives
- Capture HTTP traffic during a login attempt.
- Identify HTTP POST requests.
- Examine the information transmitted between the client and server.
- Understand the security risks of transmitting login information over unencrypted HTTP.

## Methodology
1. Accessed the target login page using a web browser.
2. Used Wireshark to capture network traffic on the active network interface.
3. Applied the following display filters to isolate relevant traffic:
   - `http`
   - `http.request.method == "POST"`
4. Submitted dummy test credentials through the login form.
5. Examined the captured POST request and observed the transmitted login information.

## Key Findings
- The login attempt was unsuccessful, but the HTTP POST request was successfully captured.
- The captured request showed that login information was transmitted over HTTP.
- The test credentials were visible in readable form because the connection did not use HTTPS encryption.

## Security Risks
- Login information transmitted over HTTP can be intercepted by someone monitoring the network.
- Unencrypted communication increases the risk of credential exposure.
- Users may be vulnerable to interception attacks on untrusted networks.

## Recommendations
- Implement HTTPS using valid TLS certificates.
- Redirect all HTTP traffic to HTTPS.
- Configure secure cookie attributes, including `Secure` and `HttpOnly`.
- Use modern TLS configurations to protect information in transit.

## Conclusion
This exercise demonstrated how Wireshark can be used to capture and analyse HTTP login traffic. It also highlighted the importance of HTTPS encryption in protecting sensitive information transmitted between users and web applications.

**Tools and Skills:** Wireshark, cURL, HTTP traffic analysis, packet inspection, network security.

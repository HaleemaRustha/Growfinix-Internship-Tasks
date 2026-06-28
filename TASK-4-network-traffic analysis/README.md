# Task 4: Network Traffic Analysis & Packet Sniffing

## Overview

This project demonstrates the use of Wireshark to capture and analyze network traffic. A simple HTTP login page was hosted locally, and the transmitted packets were inspected to identify unencrypted credentials. The exercise highlights the importance of secure communication protocols and demonstrates how plaintext data can be intercepted over HTTP.

---

## Objective

- Capture network traffic using Wireshark.
- Analyze HTTP packets.
- Extract unencrypted login credentials.
- Understand the security risks of transmitting sensitive information over HTTP.

---

## Tools Used

- Kali Linux
- Wireshark 4.6.4
- Python 3

---

## Procedure

### 1. Packet Capture

A packet capture was started on the loopback (`lo`) interface using Wireshark.

### 2. HTTP Login Simulation

A simple Python HTTP server was created to simulate an employee login portal. The following sample credentials were submitted:

- Username: `employee`
- Password: `Password123`

Since the application used HTTP instead of HTTPS, the credentials were transmitted without encryption.

### 3. Packet Analysis

The captured packets were filtered using:

```
http
```

The following HTTP communication was observed:

- GET request
- HTTP 200 OK response
- POST request
- HTTP 200 OK response

Inspection of the POST request revealed the submitted credentials:

```
Form item: username = employee
Form item: password = Password123
```

This demonstrates that HTTP transmits sensitive information in plaintext.

---

## Findings

- Successfully captured HTTP network traffic.
- Identified GET and POST requests.
- Extracted plaintext credentials from the POST request.
- Demonstrated the security risks associated with unencrypted HTTP communication.

---

## Security Recommendations

- Use HTTPS instead of HTTP.
- Encrypt all authentication traffic using TLS.
- Avoid transmitting sensitive information over unencrypted connections.
- Implement secure authentication and encryption best practices.

---

## Repository Structure

```
Task4-Network-Traffic-Analysis/
│
├── README.md
├── server.py
├── task4_capture.pcapng
└── screenshots/
    ├── login-page.png
    ├── packet-capture.png
    ├── http-post-request.png
    └── credentials-found.png
```

---

## Skills Demonstrated

- Network Traffic Analysis
- Packet Capture
- Packet Sniffing
- HTTP Protocol Analysis
- Wireshark Filtering
- Credential Analysis
- Basic Network Security

---

## Conclusion

This project demonstrates how network traffic can be captured and analyzed using Wireshark. By inspecting HTTP packets, plaintext credentials were successfully identified, reinforcing the importance of using HTTPS to protect sensitive information during transmission.

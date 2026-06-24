# Task 1 – OSINT Reconnaissance Report

## 1. Objective
The objective of this task was to perform passive reconnaissance on a target organization using Open Source Intelligence (OSINT) techniques. The goal was to identify publicly exposed subdomains, analyze infrastructure exposure, and evaluate potential security observations without performing any intrusive or active exploitation techniques.

---

## 2. Target Information
- Organization: OWASP Foundation  
- Primary Domain: owasp.org  
- Assessment Type: Passive Reconnaissance (OSINT)  
- Scope: Publicly accessible internet-facing assets only  

---

## 3. Tools Used
- theHarvester – for gathering subdomains and public information  
- Sublist3r – for passive subdomain enumeration  
- Shodan – for identifying exposed services and ports  
- curl – for validating HTTP response codes of discovered subdomains  

---

## 4. Methodology

### 4.1 Subdomain Enumeration
Passive reconnaissance tools (theHarvester and Sublist3r) were used to identify publicly discoverable subdomains associated with the target domain.

### 4.2 Service Validation
Each discovered subdomain was tested using curl to determine HTTP response codes and classify services as active, redirected, or inactive.

### 4.3 Infrastructure Analysis
DNS resolution data and CDN behavior were analyzed to understand the external exposure of the target infrastructure.

### 4.4 Credential Exposure Check
A basic attempt was made to identify exposed credentials or secrets using public GitHub search. The attempt was limited due to API authentication restrictions.

---

## 5. Findings

### 5.1 Subdomains Discovered
A total of 19 subdomains were identified. Key examples include:

- wiki.owasp.org  
- genai.owasp.org  
- securecodingdojo.owasp.org  
- secureflag.owasp.org  
- www.owasp.org  

These subdomains indicate a segmented infrastructure supporting documentation, training, experimental, and security-related services.

---

### 5.2 HTTP Response Analysis

- **200 OK**: Indicates active services (example: genai.owasp.org)  
- **301 Moved Permanently**: Indicates legacy or redirected services  
- **302 Found**: Indicates temporary redirects or dynamic routing  

Most discovered subdomains returned either 301 or 302 responses, suggesting centralized routing or migration of services.

---

### 5.3 Infrastructure Observations
- All resolved IP addresses were associated with Cloudflare CDN  
- No origin server IP addresses were directly exposed  
- No open ports or exposed services were identified through Shodan  
- Infrastructure appears logically segmented by service type  

---

### 5.4 Credential Exposure Check
Automated GitHub-based searches were restricted due to API authentication requirements. Within the limited manual scope, no exposed credentials or sensitive keys were identified.

---

## 6. Security Assessment

| Finding | Severity | Observation |
|--------|----------|-------------|
| Multiple subdomains (19 total) | Low | Normal for large organizations |
| Cloudflare CDN usage | Positive | Origin infrastructure hidden |
| Experimental subdomains | Low | Potential future misconfiguration risk |
| No exposed ports detected | Positive | Strong external exposure control |
| No credential leaks found | Positive | No immediate data exposure |

---

## 7. Conclusion
The external attack surface of the OWASP Foundation appears well-structured and securely managed. While multiple subdomains exist, they are organized and largely protected behind Cloudflare infrastructure.

No critical vulnerabilities, exposed services, or credential leaks were identified during this passive reconnaissance exercise.

---

## 8. Disclaimer
This assessment was conducted as part of a cybersecurity internship assignment. All data was collected using publicly available information only. No unauthorized access, scanning, or exploitation was performed.

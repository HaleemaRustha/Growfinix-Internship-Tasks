# Task 1 – OSINT Reconnaissance

## Objective
To perform passive reconnaissance on a target organization using open-source intelligence (OSINT) tools and analyze its publicly available attack surface.



## Target
- Organization: OWASP Foundation  
- Domain: owasp.org  
- Type: Passive Reconnaissance (no intrusion or exploitation performed)



## Tools Used
- theHarvester – subdomain and public data collection  
- Sublist3r – passive subdomain enumeration  
- Shodan – exposed service analysis  
- curl – HTTP response validation  



## Methodology

### Subdomain Enumeration
Passive reconnaissance was performed using theHarvester and Sublist3r to identify publicly available subdomains associated with the target domain.

### Service Validation
HTTP response codes were analyzed using curl to determine whether discovered subdomains were active, redirected, or inactive.

### Infrastructure Analysis
DNS resolution patterns, CDN usage, and IP responses were analyzed to understand external exposure.

### Credential Exposure Check
Attempts were made to identify exposed credentials via public GitHub searches. Results were limited due to API authentication restrictions.



## Findings

### Subdomains Discovered
A total of 19 subdomains were identified, including:

- wiki.owasp.org  
- genai.owasp.org  
- securecodingdojo.owasp.org  
- secureflag.owasp.org  
- www.owasp.org  


### Service Status Analysis

- 200 OK: Active services (e.g., genai.owasp.org)  
- 301: Permanent redirects (legacy or migrated services)  
- 302: Temporary redirects (dynamic routing services)  



### Infrastructure Observations
- All domains resolved behind Cloudflare CDN  
- No direct origin IP exposure detected  
- No open ports or exposed backend services identified via Shodan  
- Subdomains appear segmented by function (documentation, training, tools, experimental services)



### Credential Exposure Check
GitHub API-based automated searches were rate-limited, preventing a full scan. No exposed credentials were identified in manual checks performed within scope.



## Security Summary
- External security posture appears strong  
- No critical vulnerabilities identified during passive reconnaissance  
- Large but structured attack surface  
- CDN effectively masks origin infrastructure  



## Conclusion
The analysis indicates a well-structured and secured external footprint. Although multiple subdomains exist, they are organized and protected behind a CDN layer, with no direct exposure of sensitive infrastructure observed.

---

## Disclaimer
This work was performed as part of a cybersecurity internship assignment. All information was collected using publicly available sources only. No unauthorized access or exploitation was performed.

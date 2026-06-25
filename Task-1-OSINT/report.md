# Open Source Intelligence (OSINT) Reconnaissance – Task 1

## Objective

Perform passive reconnaissance on a target organization to identify exposed subdomains, map publicly available infrastructure, and surface any potentially sensitive information — without any intrusion or active exploitation.

**Target:** OWASP Foundation (owasp.org)  
**Type:** Passive Reconnaissance (OSINT only)  
**Scope:** Public-facing internet presence

---

## Tools Used

| Tool | Purpose |
|------|---------|
| theHarvester | Enumerate subdomains and public mentions |
| Sublist3r | Discover subdomains via passive sources |
| Shodan | Check for exposed ports and services |
| curl | Validate live services via HTTP response codes |

---

## Methodology

This task followed a structured passive reconnaissance approach:

1. **Subdomain Enumeration** — Identified all public subdomains associated with the target domain
2. **Live Service Validation** — Tested each subdomain for active HTTP responses
3. **Infrastructure Analysis** — Identified CDN usage, redirect behavior, and service structure
4. **Credential/Leak Check** — Checked public GitHub for accidentally exposed secrets or credentials

---

## Findings

### Subdomains Discovered — 19 Total

Notable subdomains identified:

- `wiki.owasp.org`
- `genai.owasp.org`
- `securecodingdojo.owasp.org`
- `secureflag.owasp.org`
- `www.owasp.org`
- *(+ 14 additional subdomains)*

### Live Service Analysis

| Status Code | Meaning | Examples |
|-------------|---------|---------|
| 200 OK | Active, live service | `genai.owasp.org` |
| 301 Moved Permanently | Permanent redirect | `wiki.owasp.org`, `www.owasp.org` |
| 302 Found | Temporary redirect | Several tool subdomains |

### Infrastructure Observations

- All resolved IPs pointed to **Cloudflare CDN** — origin servers are not directly exposed
- No open backend ports discovered via Shodan
- Infrastructure is well-segmented across multiple purpose-specific subdomains

### Credential / Leak Check

- GitHub API automated search was rate-limited (expected behavior without authentication)
- **No publicly exposed credentials, API keys, or sensitive data identified**

---

## Security Observations

| Finding | Severity | Notes |
|--------|---------|-------|
| Large subdomain attack surface (19 subdomains) | Low | Normal for a large org; increases monitoring scope |
| Cloudflare CDN in use | Positive | Origin servers hidden; DDoS protection active |
| Experimental subdomains present (genai, training) | Low | Worth monitoring for misconfigurations over time |
| No exposed credentials found | Positive | No leaks detected in passive scan |
| No directly exposed servers | Positive | Backend infrastructure not reachable from public internet |

---

## Conclusion

Passive reconnaissance of OWASP revealed a large but well-structured external attack surface. The organization follows good security practices — backend infrastructure is shielded behind Cloudflare, no credentials were found exposed publicly, and no open ports were directly reachable.

The 19 discovered subdomains represent a broad digital footprint that a security team should continuously monitor for misconfigurations, especially experimental or lesser-maintained services.

**This task demonstrated the first phase of a real-world security assessment: understanding what an attacker can learn before attempting any intrusion.**

---

## Disclaimer

This reconnaissance was conducted as part of a supervised cybersecurity internship for educational purposes only. No systems were accessed, exploited, or modified. All information gathered is publicly available.

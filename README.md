# Breaking-Trust-How-I-Compromised-My-College-s-Web-Infrastructure
A real-world security write-up documenting how I compromised my college’s web infrastructure by chaining weak authentication logic, missing session protections, insecure configurations, and vulnerable CMS components. This repo focuses on attacker mindset, impact, and lessons learned after responsible disclosure and patching.
# Breaking Trust: Security Assessment of a College Web Infrastructure

> All vulnerabilities documented in this repository were responsibly disclosed and patched before publication.  
> This repository is intended strictly for learning, awareness, and defensive security improvement.

---

## 📌 Overview

This repository contains a real-world security assessment write-up based on my college’s web infrastructure.  
The goal of this project is to document how multiple small security weaknesses—when chained together—can lead to a full system compromise, even in environments protected by perimeter defenses like Cloudflare and WAFs.

No zero-day vulnerabilities were used.  
The compromise resulted from broken trust assumptions, weak authentication logic, missing session protections, insecure configurations, and vulnerable CMS components.

---

## 🎯 Scope of the Assessment

The assessment focused on publicly exposed assets and included:

- Subdomain enumeration and attack surface mapping  
- Network and service enumeration  
- Web application security testing  
- Authentication and authorization testing  
- Session management and CSRF analysis  
- WordPress plugin and theme vulnerability analysis  
- Directory and endpoint fuzzing  

All testing was conducted ethically and documented responsibly.

---

## 🛠️ Tools & Techniques Used

This assessment involved a combination of manual analysis and industry-standard tools, including:

- **Burp Suite** (request interception, authentication testing)
- **Burp Suite Intruder** (behavioral testing)
- **sqlmap** (controlled backend validation)
- **Nmap** (network and service enumeration)
- **WPScan** (WordPress vulnerability enumeration)
- **Python HTTP Server** (CSRF proof-of-concept testing)
- **Directory fuzzing techniques** for exposed resource discovery

No exploit payloads or attack scripts are included in this repository.

---

## 🔎 Key Findings (High-Level)

The assessment identified multiple security issues, including:

- Authentication bypass through SQL injection
- Missing CSRF protections on sensitive actions
- Weak server hardening (e.g., TRACE enabled on IIS)
- Vulnerable WordPress plugins and themes
- Publicly exposed internal resources
- Lack of effective monitoring and detection

These issues, when chained together, enabled full compromise of backend trust.

---

## 🔁 Attack Flow (High-Level)

1. Subdomain enumeration and asset discovery  
2. Network and configuration analysis  
3. Authentication testing and bypass  
4. Backend database access  
5. Session abuse due to missing CSRF protections  
6. Expansion through WordPress vulnerabilities  
7. Discovery of additional exposed resources  
8. No detection or response during the process  

This flow highlights how real-world attacks often progress quietly.

---

## 💥 Impact Summary

The findings impacted all three components of the **CIA triad**:

- **Confidentiality**: Exposure of sensitive student, faculty, and internal data  
- **Integrity**: Risk of data modification or corruption  
- **Availability**: Potential for service disruption and data deletion  

Once authentication and database trust were broken, downstream security controls became ineffective.

---

## 🧠 Why This Matters

This assessment demonstrates that:

- Perimeter defenses alone are not sufficient
- Authentication is the most critical trust boundary
- Small misconfigurations can cascade into major breaches
- Monitoring and detection are as important as prevention

Security must be continuously validated, not assumed.

---

## 🛡️ Remediation Summary

Key defensive improvements include:

- Enforcing parameterized queries and strict input validation
- Implementing CSRF protection on all state-changing actions
- Hardening servers and disabling unnecessary features
- Reducing CMS attack surface and patching components
- Monitoring authentication behavior and database access patterns

---

## ⚠️ Disclaimer

This repository does **not** contain exploit code, payloads, or instructions.  
All findings were responsibly disclosed and patched prior to publication.  
The content is shared for **educational and defensive awareness purposes only**.

---

## ✍️ Author

Written by a cybersecurity student and ethical hacking practitioner, documenting real-world learning through responsible security research.

---

## 📄 Related Write-Up

A detailed narrative version of this assessment is available on Medium.  
https://medium.com/@tagirisaharshavardhan

---

## ⭐ Final Note

No zero-days.  
No brute force.  
No social engineering.

Just broken trust—and no one watching.

That’s how most real-world breaches begin.

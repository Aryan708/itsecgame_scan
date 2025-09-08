# Security Assessment Report

## 1. Executive Summary
A security assessment was performed on **itsecgames.com** (IP: 31.3.96.40). 
The site hosts **bWAPP**, a deliberately vulnerable web application. 
Findings include outdated services, missing security headers, and exposure of sensitive files. 

---

## 2. Scope & Methodology
- Tools: Nmap, WhatWeb, manual header analysis. 
- Focus: Open ports, web technologies, misconfigurations. 

---

## 3. Findings

### 3.1 Open Ports (Nmap)
- **22/tcp (SSH):** OpenSSH 6.7p1 (outdated). 
- **80/tcp (HTTP):** Apache, serving **bWAPP**. 
- **443/tcp (HTTPS):** Apache + SSL, Drupal 7 CMS. 
- SSL cert valid Aug–Nov 2025. 

### 3.2 HTTP Headers
- Server: Apache. 
- Missing: `HSTS`, `CSP`, `X-Frame-Options`, `X-Content-Type-Options`.
- Risk: Clickjacking, XSS, downgrade attacks. 

### 3.3 Web Fingerprinting (WhatWeb)
- Tech: Apache, HTML5, custom scripts. 
- Location: Netherlands. 
- Title: *bWAPP, a buggy web application!* 

### 3.4 Sensitive Files (robots.txt)
- Disallowed: `/install.php`, `/cron.php`, `/INSTALL.txt`, `/LICENSE.txt`. 
- Risk: Information disclosure. 

---

## 4. Risks & Recommendations
- **Outdated SSH:** Upgrade OpenSSH, disable weak ciphers. 
- **Apache Exposure:** Update, hide version info. 
- **Missing Headers:** Apply HSTS, CSP, XFO, XCTO. 
- **Drupal 7:** Upgrade to supported CMS. 
- **Robots.txt Exposure:** Remove/secure sensitive files. 
- **bWAPP Public Access:** Restrict to internal/VPN only. 

---

## 5. Conclusion
The target hosts intentionally vulnerable apps. 
However, public exposure poses severe risks. 
Immediate action: patch services, apply headers, restrict access. 






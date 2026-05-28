# FUTURE_CS_01
# 🔐 FUTURE_CS_01 – Vulnerability Assessment Report

**Future Interns | Cyber Security Track | Task 1**

---

## 📋 Overview

This repository contains my completed work for **Task 1** of the Future Interns Cyber Security Internship Programme. The task involved conducting a passive, ethical vulnerability assessment on a publicly accessible website and documenting all findings in a professional report.

The goal was not to hack or exploit anything — but to approach the target the way a real security consultant would: identify weaknesses, explain what they mean in plain language, and recommend practical fixes.

---

## 🌐 Target Website

| Detail | Info |
|---|---|
| **Site** | [demo.testfire.net](https://demo.testfire.net) |
| **Organisation** | Altoro Mutual (IBM demo banking application) |
| **IP Address** | 65.61.137.117 |
| **Assessment Type** | Passive / Read-Only |
| **Scope** | Public-facing pages only |

> ⚠️ This is a deliberately vulnerable demo site created by IBM for security training purposes. It is legal and ethical to test. No real users or real data were involved.

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| [SecurityHeaders.com](https://securityheaders.com) | HTTP security header analysis |
| **Nmap 7.95** (Kali Linux) | Port scanning and service version detection |
| **Firefox DevTools** | Browser console and network inspection |
| **OWASP ZAP** | Passive web vulnerability scanning |

---

## 🔍 Assessment Phases

### Phase 1 – Security Header Analysis
Used SecurityHeaders.com to check which HTTP security headers were missing from the site's responses. The site received an overall grade of **F**, with 6 critical headers absent.

### Phase 2 – Network Port Scan (Nmap)
Ran `nmap -sV -Pn demo.testfire.net` from Kali Linux to identify open ports and exposed services. Found 3 open ports, including the high-risk port 8080.

### Phase 3 – Browser Console Inspection
Opened the site in Firefox with DevTools to check for console warnings. Found a missing DOCTYPE declaration causing the page to render in Almost Standards Mode.

---

## 📊 Findings Summary

| ID | Vulnerability | Source | Risk Level |
|---|---|---|---|
| VUL-001 | Missing HSTS Header | SecurityHeaders.com | 🟡 Medium |
| VUL-002 | Missing Content-Security-Policy | SecurityHeaders.com | 🔴 High |
| VUL-003 | Missing X-Frame-Options | SecurityHeaders.com | 🟡 Medium |
| VUL-004 | Missing X-Content-Type-Options | SecurityHeaders.com | 🟡 Medium |
| VUL-005 | Missing Referrer-Policy | SecurityHeaders.com | 🟢 Low |
| VUL-006 | Missing Permissions-Policy | SecurityHeaders.com | 🟢 Low |
| VUL-007 | Port 8080 Publicly Accessible | Nmap | 🔴 High |
| VUL-008 | Server Version Disclosed | Nmap | 🟡 Medium |
| VUL-009 | Port 80 (HTTP) Left Open | Nmap | 🟡 Medium |
| VUL-010 | Missing DOCTYPE Declaration | Browser DevTools | 🟢 Low |

**Total: 10 findings — 2 High, 5 Medium, 3 Low**

---

## 📁 Repository Structure

```
FUTURE_CS_01/
│
├── README.md                          ← You are here
│
├── report/
│   └── FUTURE_CS_01_Vulnerability_Assessment_Report.docx
│
└── evidence/
    ├── securityheaders_scan.png       ← Phase 1: Missing headers screenshot
    ├── nmap_scan.png                  ← Phase 2: Nmap terminal output
    └── browser_console.png           ← Phase 3: DevTools console warning
```

---

## 📄 Deliverable

The full **Vulnerability Assessment Report** is available in the `/report` folder. It includes:

- Executive summary with findings overview
- Detailed breakdown of all 10 vulnerabilities
- Business impact explanation for each finding
- Practical remediation steps written in plain language
- Prioritised recommendations table

---

## ⚙️ Nmap Command Used

```bash
nmap -sV -Pn demo.testfire.net -oN nmap_scan.txt
```

**Output:**
```
PORT       STATE   SERVICE    VERSION
80/tcp     open    http       Apache Tomcat/Coyote JSP engine 1.1
443/tcp    open    ssl/http   Apache Tomcat/Coyote JSP engine 1.1
8080/tcp   open    http       Apache Tomcat/Coyote JSP engine 1.1
```

---

## ⚠️ Ethics Statement

This assessment was conducted strictly within ethical and legal boundaries:

- ✅ Only public-facing pages were analysed
- ✅ No login credentials were used
- ✅ No vulnerabilities were exploited
- ✅ No denial-of-service or brute force attempts were made
- ✅ The target site is a legal practice environment designed for security testing

---

## 👤 About

**Intern:** Aphelele  
**Track:** Cyber Security  
**Programme:** Future Interns Internship 2026  
**Task:** Task 1 – Vulnerability Assessment Report for a Live Website  
**Repository:** FUTURE_CS_01

---

*Prepared as part of the Future Interns Cyber Security Internship Programme. All testing was passive and read-only.*

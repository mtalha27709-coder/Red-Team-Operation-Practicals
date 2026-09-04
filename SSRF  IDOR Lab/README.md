# 🔴 IDOR — Insecure Direct Object Reference Testing

<p align="center">

![Platform](https://img.shields.io/badge/Platform-Kali%20Linux-blue?style=for-the-badge)
![Vulnerability](https://img.shields.io/badge/Vulnerability-IDOR-red?style=for-the-badge)
![OWASP](https://img.shields.io/badge/OWASP-A01%20Broken%20Access%20Control-orange?style=for-the-badge)
![Severity](https://img.shields.io/badge/Severity-High-critical?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

</p>

---

## 📌 Overview

This project demonstrates **IDOR (Insecure Direct Object Reference)** testing against intentionally vulnerable web applications in a controlled lab environment.

The assessment focused on modifying object identifiers in HTTP requests to determine whether proper server-side authorization controls were enforced.

> ⚠️ **Disclaimer:** Testing was performed only against authorized and intentionally vulnerable laboratory applications.

---

## 🧪 Lab Environment

| Component | Details |
|---|---|
| Attacker | Kali Linux |
| Target | OWASP Juice Shop / DVWA |
| Testing Type | Web Application Penetration Testing |
| Vulnerability | IDOR |
| OWASP Category | A01: Broken Access Control |
| Severity | High |

---

## 🛠️ Tools Used

- Burp Suite Community Edition
- Browser Developer Tools
- OWASP Juice Shop
- DVWA
- Kali Linux

---

## 🎯 Objective

- Identify requests containing object references.
- Modify object identifiers.
- Analyze server responses.
- Test authorization enforcement.
- Determine whether unauthorized resources can be accessed.

---

# 🔎 Testing Methodology

### 1️⃣ Identify Object Reference

A request containing an object identifier was identified.

```
http
GET /profile?id=1
```


---

## 💥 Observation
After changing the object identifier:
```
id=1  →  id=2
```
The application returned information belonging to another user.
This indicated that proper server-side authorization checks were not being enforced.

---

## 📊 Security Impact

A successful IDOR vulnerability may allow an attacker to:

Access unauthorized user information
View private account data
Access other users' resources
Modify unauthorized resources
Delete resources belonging to other users
```
Severity: High
```
---

## 🛡️ Recommendations
Implement server-side authorization checks.
Verify resource ownership for every request.
Do not rely on hidden or predictable IDs.
Use indirect object references where appropriate.
Apply proper access-control policies.
Test authorization controls during security assessments.


---

## 🧠 Skills Demonstrated

IDOR Testing
Broken Access Control
Burp Suite
HTTP Request Analysis
Web Application Penetration Testing
Authorization Testing
OWASP Top 10
Vulnerability Assessment
```
Security Reporting - High
```
---

## 🏁 Conclusion

This lab demonstrated how improper authorization checks can allow authenticated users to access resources belonging to other users by modifying object identifiers.
The exercise strengthened practical skills in IDOR testing, access-control assessment, Burp Suite, HTTP analysis, and web application security.


---


## 👨‍💻 Author
## Muhammad Talha

Cybersecurity | Web Security | SOC | Red Team | Blue Team | Detection Engineering

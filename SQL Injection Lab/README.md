# 🔴 SQL Injection Authentication Bypass

<p align="center">

![Platform](https://img.shields.io/badge/Platform-Kali%20Linux-blue?style=for-the-badge)
![Vulnerability](https://img.shields.io/badge/Vulnerability-SQL%20Injection-red?style=for-the-badge)
![OWASP](https://img.shields.io/badge/OWASP-A03%20Injection-orange?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

</p>

---

## 📌 Overview

This project demonstrates **SQL Injection (SQLi) Authentication Bypass** testing against intentionally vulnerable web applications in a controlled lab environment.

The assessment focused on identifying whether user-controlled login parameters could manipulate backend SQL queries and bypass authentication controls.

> ⚠️ **Disclaimer:** Testing was performed only against authorized and intentionally vulnerable laboratory applications.

---

## 🧪 Lab Environment

| Component | Details |
|---|---|
| Attacker | Kali Linux |
| Target | OWASP Juice Shop / DVWA |
| Testing Type | Web Application Penetration Testing |
| Vulnerability | SQL Injection |
| OWASP Category | A03: Injection |

---

## 🛠️ Tools Used

- Burp Suite Community Edition
- Browser Developer Tools
- OWASP Juice Shop
- DVWA
- Kali Linux

---

## 🎯 Objective

- Identify SQL injection points in login functionality.
- Capture and analyze authentication requests.
- Test user-controlled input parameters.
- Determine whether authentication can be bypassed.
- Document security impact and mitigations.

---

# 🔎 Testing Methodology

### 1️⃣ Identify Login Functionality

The application's login page and authentication parameters were identified.

### 2️⃣ Capture Request

Burp Suite was used to intercept and inspect the login request.

### 3️⃣ Input Manipulation

Controlled SQL injection test input was placed into the authentication parameter.

Example:

```text
' OR 1=1--
```



---

# 📊 Security Impact

Successful SQL Injection may allow an attacker to:
- Bypass authentication
- Access unauthorized accounts
- Retrieve database information
- Modify database records
- Potentially compromise application data

- Severity: High / Critical


---

# 🛡️ Recommendations
- Use prepared statements.
- Implement parameterized SQL queries.
- Validate user input.
- Apply proper database access controls.
- Avoid dynamically constructed SQL queries.
- Use secure authentication mechanisms.
- Monitor and log suspicious SQL injection attempts.


---

# 🧠 Skills Demonstrated
- SQL Injection Testing
- Authentication Bypass
- Burp Suite
- HTTP Request Analysis
- Web Application Penetration Testing
- OWASP Top 10
- Input Validation Testing
- Vulnerability Assessment
- Security Reporting

---


# 📂 Project Structure
```
SQL-Injection-Authentication-Bypass/
│
├── README.md
├── screenshots/
├── evidence/
└── report/
```
---

# 🏁 Conclusion

This lab demonstrated how improper handling of user input can allow SQL Injection-based authentication bypass.
The exercise strengthened practical skills in Burp Suite, HTTP request analysis, SQLi testing, authentication assessment, and secure application development.

---


# 👨‍💻 Author
# Muhammad Talha

Cybersecurity | Web Security | SOC | Red Team | Blue Team | Detection Engineering
- Critical / High


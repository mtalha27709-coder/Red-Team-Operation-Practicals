# 🔐 API Security Testing — OWASP Juice Shop

### API Authentication • Authorization • JWT Security • Parameter Manipulation • Information Disclosure

---

## 📌 Project Overview

**API Security Testing** is a hands-on Web Application Security project focused on assessing the security of REST API authentication and authorization mechanisms within the **OWASP Juice Shop** application.

The assessment was conducted from an offensive security perspective using **Burp Suite Community Edition**, **Browser Developer Tools**, and **Kali Linux**.

The primary focus was to determine whether API authentication controls could be bypassed, whether invalid authentication data could provide unauthorized access, and whether API parameter manipulation could expose sensitive user information.

The assessment followed a structured security-testing lifecycle:

```text
Identify
   ↓
Intercept
   ↓
Manipulate
   ↓
Test
   ↓
Analyze
   ↓
Validate
   ↓
Document
```

---

# 🎯 Assessment Objectives

The project focused on evaluating the following API security controls:

* API authentication enforcement
* JWT-based authentication
* Authorization behavior
* Authentication cookie handling
* Invalid token handling
* API parameter manipulation
* Sensitive information exposure
* Unauthorized access scenarios
* API response behavior

The goal was to validate whether the API maintained appropriate security controls when authentication mechanisms and request parameters were modified.

---

# 🧪 Lab Environment

| Component        | Details                             |
| ---------------- | ----------------------------------- |
| Target           | OWASP Juice Shop                    |
| Testing Type     | Web Application Penetration Testing |
| Security Focus   | API Security                        |
| Operating System | Kali Linux                          |
| Proxy            | Burp Suite Community Edition        |
| Browser Analysis | Browser Developer Tools             |
| Authentication   | JWT                                 |
| Primary API      | `/rest/user/whoami`                 |

---

# 🛠️ Tools & Technologies

### Security Testing

* **Burp Suite Community Edition**
* **Browser Developer Tools**
* **Kali Linux**

### Target Application

* **OWASP Juice Shop**

### Security Concepts

* REST API Security
* Authentication Testing
* Authorization Testing
* JWT Security
* Session / Cookie Security
* Parameter Manipulation
* Information Disclosure
* Web Application Penetration Testing

---

# 🔬 Testing Methodology

The assessment was performed using a manual API testing workflow.

### 01 — Endpoint Identification

Identify an API endpoint responsible for returning authenticated user information.

### 02 — Baseline Analysis

Capture and analyze the normal authenticated request.

### 03 — Authentication Testing

Modify or remove authentication information to evaluate enforcement.

### 04 — JWT Testing

Test valid and invalid JWT authentication scenarios.

### 05 — Session Testing

Remove the authentication cookie and observe application behavior.

### 06 — Parameter Manipulation

Modify API parameters to determine whether additional information can be exposed.

### 07 — Response Analysis

Compare HTTP status codes and JSON responses across different test cases.

### 08 — Security Validation

Determine whether the observed behavior represents an authentication bypass, authorization issue, or information disclosure vulnerability.

---

# 🎯 Target API Endpoint

```http
GET /rest/user/whoami?fields=email
```

The endpoint was selected because it exposes information associated with the currently authenticated user, making it useful for testing:

* Authentication
* Authorization
* JWT handling
* Session state
* Parameter manipulation
* Information disclosure

---

# 🔐 Authentication Testing

## Test 01 — Valid JWT

A valid JWT was supplied with the API request.

### Request

```http
GET /rest/user/whoami?fields=email
Authorization: Bearer <Valid JWT>
```

### Response

```http
HTTP/1.1 200 OK
```

```json
{
  "user": {
    "email": "admin@juice-sh.op"
  }
}
```

### Observation

The API accepted the valid authentication token and returned the authenticated user's email address.

**Result:** ✅ Expected authenticated behavior

---

# 🚫 Test 02 — Authorization Header Removal

The `Authorization` header was removed from the request.

### Request

```http
GET /rest/user/whoami?fields=email
```

### Response

```json
{
  "user": {}
}
```

### Observation

The API did not return the authenticated user's information after the authentication header was removed.

**Result:** ✅ No sensitive information exposed

---

# 🍪 Test 03 — Authentication Cookie Removal

The authentication cookie:

```text
token
```

was removed from the request.

### Response

```json
{
  "user": {}
}
```

### Observation

The application treated the request as unauthenticated and did not return sensitive user information.

**Result:** ✅ No sensitive information exposed

---

# 🪪 Test 04 — Invalid JWT

An invalid authentication token was supplied.

### Request

```http
Authorization: Bearer abc123
```

### Response

```json
{
  "user": {}
}
```

### Observation

The invalid token did not provide access to authenticated user information.

**Result:** ✅ No authentication bypass observed

---

# 🧬 Test 05 — Parameter Manipulation

The API `fields` parameter was modified using multiple values:

```text
fields=id
fields=role
fields=password
fields=*
fields=email,password
```

### Observation

The tested requests returned:

```json
{
  "user": {}
}
```

No additional sensitive information was disclosed through the tested parameter variations.

**Result:** ✅ No excessive data exposure observed

---

# 📊 Testing Results

| Security Test                 | Result   | Observation                            |
| ----------------------------- | -------- | -------------------------------------- |
| Valid JWT                     | ✅ Passed | Authenticated data returned            |
| Missing Authorization         | ✅ Passed | No sensitive data exposed              |
| Missing Authentication Cookie | ✅ Passed | Empty user object                      |
| Invalid JWT                   | ✅ Passed | No authenticated data returned         |
| Parameter Manipulation        | ✅ Passed | No additional data exposed             |
| Information Disclosure        | ✅ Passed | No exposure identified                 |
| Authentication Bypass         | ✅ Passed | Not identified within tested scenarios |

---

# 🔎 Security Assessment

### Authentication

The API successfully processed a valid JWT and returned authenticated user information.

When authentication information was removed or invalidated, protected user information was not returned.

### Authorization

Unauthenticated requests did not expose the authenticated user's information during the tested scenarios.

### JWT Handling

An invalid JWT did not result in access to authenticated user information.

### Parameter Security

Multiple `fields` parameter variations were tested without observing additional sensitive information.

### Information Disclosure

No sensitive information disclosure was identified within the tested endpoint and scenarios.

---

# 🧠 Attack Surface Tested

```text
                 API Endpoint
                      │
          ┌───────────┴───────────┐
          │                       │
   Authentication             Parameters
          │                       │
     ┌────┼────┐            ┌─────┴─────┐
     │    │    │            │     │     │
   Valid Missing Invalid    ID   Role Password
   JWT   JWT    JWT               │
     │    │    │                 *
     └────┴────┘
          │
          ▼
    Response Analysis
          │
          ▼
   Sensitive Data Check
```

---

# 🛡️ Security Controls Validated

The assessment provided practical validation of:

* Authentication enforcement
* JWT-based access control
* Unauthenticated request handling
* Invalid token handling
* Authentication cookie dependency
* API parameter behavior
* Sensitive information protection

---

# 📈 Key Findings

### Finding 01 — Authentication Enforcement

**Status:** 🟢 No issue identified

Requests without valid authentication did not expose authenticated user information.

---

### Finding 02 — Invalid JWT Handling

**Status:** 🟢 No issue identified

The tested invalid JWT did not provide access to protected user information.

---

### Finding 03 — Parameter Manipulation

**Status:** 🟢 No issue identified

Manipulation of the tested `fields` parameter did not expose additional sensitive information.

---

### Finding 04 — Sensitive Information Disclosure

**Status:** 🟢 No issue identified

No sensitive information was observed through the tested unauthenticated and parameter-manipulation scenarios.

---

# 🧰 Practical Skills Demonstrated

## API Security

* REST API testing
* Authentication testing
* Authorization testing
* JWT analysis
* Session testing
* Parameter manipulation
* Information disclosure testing

## Offensive Security

* HTTP request interception
* Request modification
* Authentication manipulation
* Token testing
* Response analysis
* Security control validation

## Web Application Security

* API attack-surface analysis
* Access-control testing
* Authentication assessment
* Security testing methodology
* Evidence-based reporting

---

# 📂 Project Structure

```text
API-Security-Testing/
│
├── README.md
│
├── Authentication/
│   ├── Valid-JWT/
│   ├── Missing-Authorization/
│   ├── Missing-Cookie/
│   └── Invalid-JWT/
│
├── Parameter-Manipulation/
│   ├── fields-id/
│   ├── fields-role/
│   ├── fields-password/
│   ├── fields-all/
│   └── fields-email-password/
│
├── Screenshots/
│   ├── Authenticated-Request/
│   ├── Missing-Authorization/
│   ├── Missing-Cookie/
│   ├── Invalid-JWT/
│   └── Parameter-Testing/
│
├── Reports/
│   └── API-Security-Assessment.pdf
│
└── Notes/
    └── Testing-Notes.md
```

---

# 📸 Evidence Collection

The project documents practical evidence from the testing process, including:

* Authenticated API requests
* JWT-bearing requests
* Modified HTTP requests
* Missing authentication scenarios
* Invalid JWT testing
* Authentication cookie manipulation
* Parameter manipulation
* JSON API responses
* Security observations

This evidence demonstrates the testing process and provides traceability between each test case and its observed result.

---

# 🎓 Learning Outcomes

This project provided practical experience in:

* Understanding REST API communication
* Working with JWT-based authentication
* Intercepting API traffic using Burp Suite
* Modifying HTTP headers
* Testing authentication enforcement
* Testing invalid authentication tokens
* Manipulating API parameters
* Analyzing JSON responses
* Evaluating sensitive data exposure
* Documenting security testing results
* Following a structured penetration-testing methodology

---

# 💼 Career Relevance

The skills demonstrated in this project are directly relevant to:

* **Web Application Penetration Tester**
* **API Security Tester**
* **Application Security Analyst**
* **Junior Penetration Tester**
* **Vulnerability Assessment Analyst**
* **Offensive Security Analyst**
* **Security Analyst**
* **SOC Analyst**

The project also complements Blue Team and Detection Engineering work by developing an attacker-side understanding of how authentication and API access controls are tested.

---

# 🚀 Project Value

This project demonstrates the ability to move beyond basic vulnerability scanning and perform **manual API security validation**.

The assessment involved:

```text
Observe
  ↓
Understand
  ↓
Intercept
  ↓
Manipulate
  ↓
Compare
  ↓
Validate
  ↓
Document
```

This workflow reflects the core mindset required for practical web application security testing.

---

# 🏁 Conclusion

The **API Security Testing** project demonstrates a structured assessment of authentication, authorization, JWT handling, session behavior, parameter manipulation, and information disclosure within the OWASP Juice Shop application.

Multiple authentication and manipulation scenarios were tested, including:

* Valid JWT authentication
* Missing authentication headers
* Missing authentication cookies
* Invalid JWT tokens
* API parameter manipulation

Based on the tested endpoint and scenarios, **no authentication bypass or excessive sensitive information exposure was identified**.

The project demonstrates practical experience with **Burp Suite, API request manipulation, authentication testing, response analysis, and web application security assessment**.

---

## 👨‍💻 Author

### Muhammad Talha

**Cybersecurity | SOC Analyst | Detection Engineering | Threat Hunting | Blue Team | Web & API Security**

**Core Areas:**

`SOC Operations` • `Detection Engineering` • `Threat Hunting` • `Incident Response` • `Web Security` • `API Security` • `Network Security` • `MITRE ATT&CK`

---

## ⚠️ Disclaimer

This project was performed against **OWASP Juice Shop**, an intentionally vulnerable security-training application, within a controlled laboratory environment.

All testing was conducted for educational and authorized cybersecurity purposes.

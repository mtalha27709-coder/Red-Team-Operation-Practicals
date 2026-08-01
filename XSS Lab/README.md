# Cross-Site Scripting (XSS) Testing

## Lab Environment

**Target Application:**  
OWASP Juice Shop

**Testing Type:**  
Web Application Penetration Testing


## Tools Used

- Burp Suite Community Edition
- Browser Developer Tools
- OWASP Juice Shop
- Kali Linux


---

# Vulnerability

**Cross-Site Scripting (XSS)**


## OWASP Category

**OWASP Top 10 → A03: Injection**


---

## Objective

- To test whether the application properly validates and sanitizes user input before displaying it in the browser.


---

## Testing Method

The following steps were performed:

1. Identified input fields accepting user-controlled data.

2. Injected JavaScript payloads into the input field.

3. Observed application behavior and browser response.


---

## Payloads Used

Basic XSS Payload:

<script>alert(1)</script>



---



## Observation

- The application processed the injected JavaScript code.

- A browser popup was displayed:

1

- This confirmed that user input was executed by the browser.



---



## Impact

An attacker may be able to:

- Execute malicious JavaScript in a victim's browser.
- Steal user session information.
- Perform actions on behalf of another user.
- Modify webpage content.


---



## Security Recommendation

To prevent XSS attacks:

- Implement proper input validation.
- Encode user output before displaying it.
- Use Content Security Policy (CSP).
- Avoid directly rendering untrusted user input.



---



## Severity

- High
# SQL Injection Authentication Bypass Testing



## Lab Environment



## Target Application:  

OWASP Juice Shop / DVWA Lab



## Testing Type: 

Web Application Penetration Testing





## Tools Used



- Burp Suite Community Edition
- Browser Developer Tools
- OWASP Juice Shop
- DVWA
- Kali Linux





---



# Vulnerability



## SQL Injection (SQLi)





## OWASP Category



## OWASP Top 10 → A03: Injection





---



## Objective



- To test whether the application's login mechanism is vulnerable to - - SQL injection attacks and whether authentication can be bypassed.





---


## Testing Method



The following steps were performed:
1. Identified login input fields.
2. Captured login request using Burp Suite.
3. Injected SQL payloads into authentication parameters.
4. Analyzed server response.




---



## Test Payload



- SQL Injection Payload:

' OR 1=1--


---

## Example Testing



## Normal Login:
- Username:   admin
- Password:  password



## Modified Input:

- Username:  ' OR 1=1--
- Password:   anything


---


## Observation



- The application processed the injected SQL statement.
- The authentication mechanism was bypassed successfully.


---



## Impact



- An attacker may be able to:
- Bypass login authentication.
- Access unauthorized accounts
- Retrieve sensitive information from the database.
- Modify or delete database records.


---


## Security Recommendation

To prevent SQL Injection:

- Use prepared statements.
- Use parameterized queries.
- Validate and sanitize user input.
- Apply least privilege database permissions.
- Avoid dynamically building SQL queries.



---

## Severity

- Critical / High


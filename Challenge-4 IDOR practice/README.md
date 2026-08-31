# IDOR (Insecure Direct Object Reference) Testing


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



## Insecure Direct Object Reference (IDOR)




## OWASP Category



## OWASP Top 10 → A01: Broken Access Control## 


---



## Objective



- To test whether an authenticated user can access another user's data by modifying object identifiers in requests.





---



## Testing Method



The following steps were performed:



1. Identified requests containing object references or IDs.
2. Captured the request using Burp Suite.
3. Modified the object identifier value.
4. Compared the server response before and after modification.



---



## Test Case

- Original Request Parameter:
id=1
- Modified Parameter:
id=2




---


## Example Request



- Before modification:
GET /profile?id=1



- After modification:

GET /profile?id=2


---


## Observation



After changing the object identifier:

- The application returned another user's information.
- Authorization checks were not properly enforced.


---



## Impact



An attacker may be able to:

- Access unauthorized user information.
- View private data of other accounts.
- Modify or delete resources belonging to other users.


---



## Security Recommendation



To prevent IDOR vulnerabilities:

- Implement server-side authorization checks.
- Do not rely only on hidden IDs.
- Use indirect references where possible.
- Verify that the logged-in user owns the requested resource.

---



## Severity

- High


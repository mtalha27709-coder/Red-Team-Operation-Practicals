# Account Registration Testing

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

## Objective

To test the user registration functionality of the application.


---

## Testing Steps

1. Opened OWASP Juice Shop.
URL:
http://192.168.245.135:3000
2. Navigated to the registration page.
3. Created a new user account.
Example:
Email:   talha@test.com
Password:
4. Intercepted the registration request using Burp Suite.
5. Analyzed request and response structure.


---

## Observation

- User account was successfully created.
- Application generated an authentication token.
- JWT token was stored in browser cookies/storage.


---

## Security Analysis

The registration functionality was working correctly.

No security issue was identified during account creation testing.


---

## Result

✅ Account Registration Testing Completed
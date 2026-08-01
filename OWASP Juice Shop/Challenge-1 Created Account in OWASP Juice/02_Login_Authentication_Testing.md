# Login Authentication Testing


## Lab Environment



## Target Application:

OWASP Juice Shop



## Testing Type:

Web Application Penetration Testing





## Tools Used



- Burp Suite Community Edition
- Browser Developer Tools
- OWASP Juice Shop
- Kali Linux





---


## Objective



- To analyze the authentication mechanism of the application and identify how user sessions are managed.



---


## Testing Steps


1. Created account credentials were used to log into the application.
Example:

- Email:
  talha@test.com
  Password:


2. Opened Burp Suite and enabled HTTP request interception.
3. Captured the login request.
- Example Endpoint:
  POST /rest/user/login
  Analyzed the request and response data.


---



## Observation



- The application uses JWT (JSON Web Token) based authentication.
- After successful login:
- Authentication token was generated.
- JWT token was stored in browser cookies.
- Token was used for authenticated requests.

---



## Example JWT Payload:

{

&#x20; "id": 24,

&#x20; "email": "user@test.com",

&#x20; "role": "customer"

}


---



## Security Analysis


- JWT authentication was implemented successfully.
- The application relies on token-based authentication for maintaining - user sessions.






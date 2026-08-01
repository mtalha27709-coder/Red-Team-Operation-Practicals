# API Security Testing

## Lab Environment

**Target Application:**  
OWASP Juice Shop

**Testing Type:**  
Web Application Penetration Testing

**Tools Used:**

- Burp Suite Community Edition
- Browser Developer Tools
- OWASP Juice Shop
- Kali Linux

---

# Objective

Analyze the application's API authentication and authorization mechanisms to determine whether sensitive information is exposed or unauthorized access is possible.

---

# Endpoint Tested

```http
GET /rest/user/whoami?fields=email
```

---

# Test 1 — Authenticated Request

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

- API successfully authenticated the request.
- User information was returned after successful authentication.
- JWT token was accepted by the server.

**Result**

? Authentication Successful

---

# Test 2 — Request Without Authorization Header

### Testing Method

The `Authorization` header was removed from the request.

### Response

```http
HTTP/1.1 200 OK
```

```json
{
  "user": {}
}
```

### Observation

- The application did not expose sensitive user information.
- Anonymous requests received an empty user object.

**Result**

? Authentication Enforcement Observed

---

# Test 3 — Request Without Authentication Cookie

### Testing Method

The authentication cookie (`token`) was removed.

### Response

```http
HTTP/1.1 200 OK
```

```json
{
  "user": {}
}
```

### Observation

- No sensitive information was returned.
- The application treated the request as unauthenticated.

**Result**

? No Sensitive Data Exposure

---

# Test 4 — Invalid JWT Testing

### Request

```http
Authorization: Bearer abc123
```

### Response

```http
HTTP/1.1 200 OK
```

```json
{
  "user": {}
}
```

### Observation

- Invalid JWT tokens were not accepted.
- The application did not expose authenticated user data.

**Result**

? Invalid Token Handled Securely

---

# Test 5 — Parameter Manipulation

### Tested Parameters

```text
fields=id
fields=role
fields=password
fields=*
fields=email,password
```

### Observation

All requests returned:

```json
{
  "user": {}
}
```

### Result

- No additional information was disclosed.
- Parameter manipulation did not expose sensitive data.

? Parameter Manipulation Tested Successfully

---

# Overall Findings

### Authentication

? JWT authentication implemented.

### Authorization

? Unauthorized requests did not expose sensitive information.

### Parameter Manipulation

? No excessive data exposure observed.

### Sensitive Information Disclosure

? No API information disclosure identified during testing.

---

# Conclusion

The tested API endpoint correctly required authentication before exposing user information. Requests made without valid authentication or with manipulated parameters returned empty responses instead of sensitive data. During this assessment, no API authentication bypass or excessive data exposure vulnerabilities were identified.

---

# Status

? API Security Testing Completed
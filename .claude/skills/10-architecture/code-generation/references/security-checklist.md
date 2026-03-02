# Security Checklist (The Big Three)

## 1. Authentication & Authorization
- [ ] Are all endpoints protected by appropriate auth?
- [ ] Does the user have the specific permission (RBAC/ABAC) for this action?
- [ ] Are session tokens securely handled (HttpOnly, Secure, SameSite)?

## 2. Input Validation & Sanitization
- [ ] Is all user-provided data validated on the **Server**?
- [ ] Are we using parameterized queries to prevent SQL Injection?
- [ ] Is output sanitized to prevent XSS (Cross-Site Scripting)?
- [ ] Are files validated for type, size, and scanned for malware?

## 3. Data Protection
- [ ] Is sensitive data encrypted at rest?
- [ ] Is all communication over TLS (HTTPS)?
- [ ] Are we leaking sensitive info in logs or error messages?
- [ ] Are secrets managed via environment variables and NOT hardcoded?

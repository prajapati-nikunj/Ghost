# Security Standards

## Secure Coding
- Never trust user input; always validate and sanitize.
- Use parameterized queries to prevent SQL injection.
- Encode output to prevent XSS.
- Implement CSRF protection for all state-changing requests.

## Authentication & Authorization
- Use strong, industry-standard hashing for passwords (e.g., Argon2, bcrypt).
- Follow the Principle of Least Privilege (PoLP).
- Implement robust RBAC/ABAC models.
- Secure secrets and environment variables.

## Compliance
- Adhere to OWASP Top 10 guidelines.
- Ensure data privacy (GDPR, HIPAA where applicable).
- Regular security audits and dependency updates.

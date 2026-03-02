# OAuth 2.0 Reference

## Authorization Code Flow (PKCE)
1. Client generates `code_verifier` and `code_challenge`.
2. Redirect user → `GET /authorize?response_type=code&code_challenge=...`
3. User authenticates → redirect back with `code`.
4. Client exchanges `code` + `code_verifier` → Access Token.

## Scopes
```
openid profile email todos:read todos:write
```

## Provider Integration
```python
# FastAPI with OAuth2
from fastapi.security import OAuth2AuthorizationCodeBearer
oauth2_scheme = OAuth2AuthorizationCodeBearer(
    authorizationUrl="/auth/authorize",
    tokenUrl="/auth/token"
)
```

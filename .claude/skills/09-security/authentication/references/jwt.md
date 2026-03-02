# JWT Authentication Reference

## Token Structure
```
Header.Payload.Signature
```

## Access + Refresh Pattern
```
Login → Access Token (15min) + Refresh Token (7d)
API Call → Authorization: Bearer <access_token>
Expired → POST /auth/refresh { refreshToken } → New access token
```

## Implementation (Python/FastAPI)
```python
from jose import jwt
from datetime import datetime, timedelta

SECRET_KEY = os.getenv("JWT_SECRET")
ALGORITHM = "HS256"

def create_access_token(user_id: str) -> str:
    payload = {"sub": user_id, "exp": datetime.utcnow() + timedelta(minutes=15)}
    return jwt.encode(payload, SECRET_KEY, algorithm=ALGORITHM)
```

## Security Rules
- Store refresh tokens in HttpOnly cookies
- Never store JWTs in localStorage
- Rotate refresh tokens on each use
- Include `iat` (issued at) for token revocation

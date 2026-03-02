# REST API Patterns

## Resource Naming
```
GET    /api/v1/todos          → List all todos
POST   /api/v1/todos          → Create a todo
GET    /api/v1/todos/:id      → Get single todo
PUT    /api/v1/todos/:id      → Replace todo
PATCH  /api/v1/todos/:id      → Partial update
DELETE /api/v1/todos/:id      → Delete todo
```

## HTTP Status Codes
| Code | Meaning | Use |
|---|---|---|
| 200 | OK | Successful GET, PUT, PATCH |
| 201 | Created | Successful POST |
| 204 | No Content | Successful DELETE |
| 400 | Bad Request | Validation failure |
| 401 | Unauthorized | Missing/invalid auth |
| 403 | Forbidden | Insufficient permissions |
| 404 | Not Found | Resource doesn't exist |
| 409 | Conflict | Duplicate resource |
| 422 | Unprocessable | Semantic validation error |
| 429 | Too Many Requests | Rate limit exceeded |
| 500 | Internal Server Error | Unhandled exception |

## Pagination (Cursor-based)
```json
GET /api/v1/todos?cursor=abc123&limit=20

{
  "data": [...],
  "pagination": {
    "nextCursor": "def456",
    "hasMore": true,
    "total": 142
  }
}
```

## Filtering & Sorting
```
GET /api/v1/todos?status=completed&sort=-createdAt&limit=10
```

## Error Response (RFC 7807)
```json
{
  "type": "https://api.example.com/errors/validation",
  "title": "Validation Error",
  "status": 422,
  "detail": "Title must be between 1 and 255 characters",
  "instance": "/api/v1/todos"
}
```

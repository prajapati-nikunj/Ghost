# API Error Handling

## Standard Error Response (RFC 7807)
```json
{
  "type": "https://api.example.com/errors/not-found",
  "title": "Resource Not Found",
  "status": 404,
  "detail": "Todo with ID 'abc123' was not found",
  "instance": "/api/v1/todos/abc123"
}
```

## Validation Error (Multiple Fields)
```json
{
  "type": "https://api.example.com/errors/validation",
  "title": "Validation Error",
  "status": 422,
  "detail": "One or more fields failed validation",
  "errors": [
    { "field": "title", "message": "Title is required" },
    { "field": "priority", "message": "Priority must be between 1 and 5" }
  ]
}
```

## Python/FastAPI Error Handler
```python
from fastapi import HTTPException, Request
from fastapi.responses import JSONResponse

class AppError(Exception):
    def __init__(self, status: int, title: str, detail: str):
        self.status = status
        self.title = title
        self.detail = detail

@app.exception_handler(AppError)
async def app_error_handler(request: Request, exc: AppError):
    return JSONResponse(status_code=exc.status, content={
        "type": f"https://api.example.com/errors/{exc.title.lower().replace(' ', '-')}",
        "title": exc.title, "status": exc.status, "detail": exc.detail,
        "instance": str(request.url),
    })
```

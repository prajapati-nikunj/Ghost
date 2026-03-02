# Docker Patterns

## Multi-Stage Build (Python/FastAPI)
```dockerfile
# Stage 1: Build
FROM python:3.12-slim AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir --prefix=/install -r requirements.txt

# Stage 2: Production
FROM python:3.12-slim
WORKDIR /app
COPY --from=builder /install /usr/local
COPY src/ ./src/
EXPOSE 8000
HEALTHCHECK --interval=30s CMD curl -f http://localhost:8000/health || exit 1
CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

## Docker Compose (Dev)
```yaml
services:
  api:
    build: ./apps/api
    ports: ["8000:8000"]
    env_file: .env
    depends_on:
      db: { condition: service_healthy }
  db:
    image: postgres:16-alpine
    environment:
      POSTGRES_DB: tododb
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: secret
    ports: ["5432:5432"]
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres"]
  redis:
    image: redis:7-alpine
    ports: ["6379:6379"]
```

## Rules
- Never use `latest` tag in production.
- Always add `.dockerignore` (exclude `node_modules`, `.env`, `.git`).
- Run as non-root user: `USER 1001`.
- Set resource limits in compose/K8s.
